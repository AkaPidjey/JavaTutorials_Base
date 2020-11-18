[Java Tutorials](README.md)

# Spring
+ [Что такое бины?](#Что-такое-бины)
+ [Чем бин отличается от POJO-класса?](#Чем-бин-отличается-от-POJO-класса)
+ [Что такое Inversion of Control и как Spring реализует этот принцип?](#Что-такое-Inversion-of-Control-и-как-Spring-реализует-этот-принцип)
+ [Что такое контекст Spring и как его создать?](#Что-такое-контекст-Spring-и-как-его-создать)
+ [Как можно связать бины?](#Как-можно-связать-бины)


+ [ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ](#ССЫЛКИ-НА-ДОПОЛНИТЕЛЬНУЮ-ИНФУ)

[к оглавлению](#spring)

## Что такое бины?
Начнем срывать покровы с самых базовых понятий Spring. Бин (bean) — это не что иное, как самый обычный объект. Разница лишь в том, что бинами принято называть те объекты, которые управляются Spring-ом и живут внутри его DI-контейнера. Бином является почти все в Spring — сервисы, контроллеры, репозитории, по сути все приложение состоит из набора бинов. Их можно регистрировать, получать в качестве зависимостей, проксировать, мокать и т.п.

[к оглавлению](#spring)

## Чем бин отличается от POJO-класса?
POJO (англ. Plain Old Java Object) — «старый добрый Java-объект», простой Java-объект, не унаследованный от какого-то специфического объекта и не реализующий никаких служебных интерфейсов сверх тех, которые нужны для бизнес-модели.

Все JavaBeans - это POJO, но не все POJO - это JavaBeans.

JavaBean - это объект Java, который удовлетворяет определенным соглашениям о программном обеспечении:
+ 1 - класс JavaBean должен реализовывать либо Serializable, либо Externalizable;
+ 2 - класс JavaBean должен иметь открытый конструктор no-arg;
+ 3 - все свойства JavaBean должны иметь общедоступные методы setter и getter (в зависимости от ситуации);
+ 4 - все переменные экземпляра JavaBean должны быть частными.

[к оглавлению](#spring)

## Что такое Inversion of Control и как Spring реализует этот принцип?

#### [Концепция Inversion of Control и основы Spring-->]( http://javatutor.net/articles/spring-basic-and-inversion-of-control )
#### [Инверсии зависимостей управления впрыском-->]( https://habr.com/ru/post/321344/ )
#### [Spring для домохозяек. Inversion of Control на практике.-->]( https://nikcode.blogspot.com/2011/09/spring-inversion-of-control.html )

[к оглавлению](#spring)

## Что такое контекст Spring и как его создать?
Контекст (а у него есть даже интерфейс — org.springframework.context.ApplicationContext) — это некоторое окружение, в котором работает приложение на Spring Framework. Страшные аббревиатуры DI, IoC — это всё про него. Собственно, контекст создаёт и хранит экземпляры классов вашего приложения, определяет их зависимости друг с другом и автоматически их задаёт.

Безусловно, для того чтобы Spring создал контекст с экземплярами классов, ему нужно предоставить дополнительную информацию — мета-данные, из каких классов/объектов состоит ваше приложение, как они создаются, какие у них есть зависимости и т. д.

Итого: Spring Context + мета-данные = работающее приложение.

Где найти контекст?
Контекст является ключевой функциональностью Spring и лежит в maven-зависимости spring-context (на момент написания — org.springframework:spring-context:5.1.4.RELEASE). Обычно эта зависимость является транзитивной для остальных проектов Spring. И если вы, например, подключаете spring-boot-starter, то она подключится автоматически, и не нужно думать про то, где её взять.

Но если вы хотите попробовать "голый" Spring, т. е. только ту часть, которая называется IoC-контейнер, то достаточно подключить лишь spring-context.

Итого: подключите org.springframework:spring-context:5.1.4.RELEASE.

Какие бывают контексты и как их создать?
У интерфейса ApplicationContext есть большое количество реализаций:
+ — ClassPathXmlApplicationContext;
+ — FileSystemXmlApplicationContext;
+ — GenericGroovyApplicationContext;
+ — AnnotationConfigApplicationContext;
+ — и даже StaticApplicationContext;
+ — а также некоторые другие.

Они отличаются друг от друга именно тем, каким способом задаются мета-данные и где хранится эта конфигурация. Например:
+ — ClassPathXmlApplicationContext — метаданные конфигурируются XML-файлом(-ами) и они лежат в classpath, т. е. в ресурсах модуля;
+ — FileSystemXmlApplicationContext — метаданные тоже конфигурируются XML-файлом(-ами), но они находятся где-то в файловой системе, например, /etc/yourapp/spring-context.xml;
+ — AnnotationConfigApplicationContext — метаданные конфигурируются с помощью аннотаций прямо на классах.

Современным способом конфигурирования считаются аннотации (AnnotationConfigApplicationContext), дальше будем создавать именно их. 

Приведём пример создания такого контекста в методе main:
```java
    @Configuration
    @ComponentScan
    public class Main {

        public static void main(String[] args) {
            AnnotationConfigApplicationContext context =
                    new AnnotationConfigApplicationContext(Main.class);
        }
    }
```
Внутри конструктора как раз и происходит инициализация контекста из мета-данных.
Как и полагается, в AnnotationConfigApplicationContext мета-данные конфигурируются аннотациями. Несложно заметить аннотацию @Configuration на Main-классе, и что он передаётся в конструктор контекста. Собственно, Main и есть описание метаданных.

[к оглавлению](#spring)

## Как можно связать бины?
Что такое привязка бинов?
Когда запускается программное приложение, совместно работают сразу несколько объектов (бинов). Также они могут использоваться независимо от других объектов.
Чтобы заставить бины работать вместе, их связывают через введение зависимостей в Spring (привязки). Когда запускается приложение на основе Spring, контекст приложения загружает определения компонентов или объектов из файла конфигурации и связывает их вместе.

Существует три способа привязки bean-компонентов в среде Spring:
+ Привязка через XML.
+ Вручную, объявив bean-компоненты с помощью Dependency Injection (DI).
+ Автоматическая привязка через аннотации.

Автоматически мы можем вводить аннотации через поля, конструкторы, геттеры/сеттеры

[к оглавлению](#spring)


## ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ

### ---Info---
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

### ---Video---

#### [Youtube/alishev/Spring Framework. Урок 1: Введение. Зачем изучать Spring?-->]( https://www.youtube.com/watch?v=5ePo08sqcpk&list=PLAma_mKffTOR5o0WNHnY0mTjKxnCgSXrZ&index=1 )
#### [YouTube/TechTrain/Евгений Борисов — Spring Patterns-->]( https://www.youtube.com/watch?v=61duchvKI6o )
#### [YouTube/Eugene Suleimanov/Spring Security + База Данных. Регистрация и авторизация(2016)-->]( https://www.youtube.com/watch?v=iivY8B5A0Tk )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

### ---Lessons---

#### [Что такое Spring Framework? От внедрения зависимостей до Web MVC-->]( https://habr.com/ru/post/490586/ )
#### [Подготовка к Spring Professional Certification. Контейнер, IoC, бины-->]( https://habr.com/ru/post/470305/ )
#### [Руководство по аннотациям Spring Framework-->]( https://coderlessons.com/articles/java/rukovodstvo-po-annotatsiiam-spring-framework )
#### [Spring Core Annotations-->]( https://www.codeflow.site/ru/article/spring-core-annotations )
#### [Understanding Dependencies-->]( https://habr.com/ru/post/349836/ )
#### [Dependency injection-->]( https://habr.com/ru/post/350068/ )
#### [Обратная сторона Spring-->]( https://habr.com/ru/post/334448/ )
#### [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 1)-->]( https://javarush.ru/groups/posts/2253-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-1 )
#### [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 2)-->]( https://javarush.ru/groups/posts/2252-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-2 )
#### [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 3)-->]( https://javarush.ru/groups/posts/2251-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-3 )
#### [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 4)-->]( https://javarush.ru/groups/posts/2250-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-4 )
#### [Spring MVC настройка без xml и web.xml-->]( https://java-master.com/spring-mvs-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%B1%D0%B5%D0%B7-xml-web-xml/ )
#### [Spring изнутри. Этапы инициализации контекста-->]( https://habr.com/ru/post/222579/ )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

### ---Forum---
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

[к оглавлению](#spring)
