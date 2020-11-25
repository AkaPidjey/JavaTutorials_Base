[Java Tutorials](README.md)

# Spring

## Spring Core
+ [Что такое бины?](#Что-такое-бины)
+ [Чем бин отличается от POJO-класса?](#Чем-бин-отличается-от-POJO-класса)
+ [Что такое Inversion of Control и как Spring реализует этот принцип?](#Что-такое-Inversion-of-Control-и-как-Spring-реализует-этот-принцип)
+ [Что такое контекст Spring и как его создать?](#Что-такое-контекст-Spring-и-как-его-создать)
+ [Как можно связать бины?](#Как-можно-связать-бины)

## Spring Security





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




## Spring_Core

### ---Info---
### ---Video---
+ [Youtube/alishev/Spring Framework. Урок 1: Введение. Зачем изучать Spring?-->]( https://www.youtube.com/watch?v=5ePo08sqcpk&list=PLAma_mKffTOR5o0WNHnY0mTjKxnCgSXrZ&index=1 )
+ [YouTube/TechTrain/Евгений Борисов — Spring Patterns-->]( https://www.youtube.com/watch?v=61duchvKI6o )
### ---Lessons---
+ [Что такое Spring Framework? От внедрения зависимостей до Web MVC-->]( https://habr.com/ru/post/490586/ )
+ [Подготовка к Spring Professional Certification. Контейнер, IoC, бины-->]( https://habr.com/ru/post/470305/ )
+ [Руководство по аннотациям Spring Framework-->]( https://coderlessons.com/articles/java/rukovodstvo-po-annotatsiiam-spring-framework )
+ [Spring Core Annotations-->]( https://www.codeflow.site/ru/article/spring-core-annotations )
+ [Understanding Dependencies-->]( https://habr.com/ru/post/349836/ )
+ [Dependency injection-->]( https://habr.com/ru/post/350068/ )
+ [Обратная сторона Spring-->]( https://habr.com/ru/post/334448/ )
+ [Spring изнутри. Этапы инициализации контекста-->]( https://habr.com/ru/post/222579/ )
+ [Как на самом деле работает @Transactional Spring?(2016)-->]( https://akorsa.ru/2016/08/kak-na-samom-dele-rabotaet-transactional-spring/ )
+ [Валидация и обработка исключений с помощью Spring(2020)-->]( https://habr.com/ru/post/523888/ )
+ [Из резюме джуна: Spring Framework — популярный фреймворк на Java(2020)-->]( https://javarush.ru/groups/posts/2921-iz-rezjume-dzhuna-spring-framework--populjarnihy-freymvork-na-java )
+ [Spring для ленивых. Основы, базовые концепции и примеры с кодом. Часть 1(2018)-->]( https://javarush.ru/groups/posts/spring-framework-java-1 )
+ [Spring для ленивых. Основы, базовые концепции и примеры с кодом. Часть 2(2018)-->]( https://javarush.ru/groups/posts/477-spring-dlja-lenivihkh-osnovih-bazovihe-koncepcii-i-primerih-s-kodom-chastjh-2 )
### ---Forum---




## Spring_MVC

### ---Info---
### ---Video---
### ---Lessons---
+ [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 1)-->]( https://javarush.ru/groups/posts/2253-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-1 )
+ [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 2)-->]( https://javarush.ru/groups/posts/2252-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-2 )
+ [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 3)-->]( https://javarush.ru/groups/posts/2251-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-3 )
+ [Знакомство с Maven, Spring, MySQL, Hibernate и первое CRUD приложение (часть 4)-->]( https://javarush.ru/groups/posts/2250-znakomstvo-s-maven-spring-mysql-hibernate-i-pervoe-crud-prilozhenie-chastjh-4 )
+ [Spring MVC настройка без xml и web.xml-->]( https://java-master.com/spring-mvs-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0-%D0%B1%D0%B5%D0%B7-xml-web-xml/ )
+ [Spring MVC 4 для начинающих. Базовые настройки. Подключение Bootstrap в Spring MVC.-->]( https://javastudy.ru/spring-mvc/spring-mvc-4-example-for-beginners/ )
+ [Spring MVC и аннотация @ModelAttribute-->](https://www.codeflow.site/ru/article/spring-mvc-and-the-modelattribute-annotation )
### ---Forum---




## Spring_Security

### ---Info---
+ [Online Bcrypt Hash Generator & Checker-->]( https://bcrypt-generator.com/ )
### ---Video---
+ [YouTube/Eugene Suleimanov/Spring Security + База Данных. Регистрация и авторизация(2016)-->]( https://www.youtube.com/watch?v=iivY8B5A0Tk )
+ [YouTube/doIT/Веб-разработка на Java. Spring Security. Часть 1.(2018)-->]( https://www.youtube.com/watch?v=MH09q37wHUA )
+ [YouTube/GrabDuck/Spring на практике - как настроить свой UserService в Spring Security-->]( https://www.youtube.com/watch?v=mX2kovQUQAo&list=PLaWfw53gNyzaDTEmrlCCj1jjqr6770Nnp&index=14)
### ---Lessons---
+ [Краткий обзор Spring Security-->]( https://habr.com/ru/post/203318/ )
+ [Быстрый старт в Spring Security(2014)-->]( https://devcolibri.com/%D0%B1%D1%8B%D1%81%D1%82%D1%80%D1%8B%D0%B9-%D1%81%D1%82%D1%80%D0%B0%D1%82-%D0%B2-spring-security/ )
+ [Безопасность Web-приложения-->]( https://spring-projects.ru/guides/securing-web/ )
+ [Добавление Spring Security в проект – настройки по умолчанию(2020)-->]( https://sysout.ru/dobavlenie-spring-security-v-proekt-nastrojki-po-umolchaniyu/ )
+ [Как настроить авторизацию в Spring Security(2020)-->]( https://sysout.ru/kak-nastroit-avtorizatsiyu-v-spring-security/ )
+ [Как устроена Аутентификация в Spring Security(2020)-->]( https://sysout.ru/kak-ustroena-autentifikatsiya-v-spring-security/ )
+ [Пользовательская аутентификация в Spring Security(2020)-->]( https://sysout.ru/polzovatelskaya-autentifikatsiya/ )
+ [Настройка JDBC-аутентификации в Spring Security(2020)-->]( https://sysout.ru/nastrojka-jdbc-autentifikatsii-v-spring-security/ )
+ [Spring Security-->]( https://javastudy.ru/frameworks/spring/spring-security/ )
### ---Forum---



## Spring_Boot

### ---Info---
+ [Spring Boot — Краткое руководство(2019)-->]( https://coderlessons.com/tutorials/java-tekhnologii/learn-spring-boot/spring-boot-kratkoe-rukovodstvo )
+ [Руководства Spring Boot-->]( https://o7planning.org/ru/11669/spring-boot )
### ---Video---
+ [YouTube/letsCode/Spring Boot: делаем простое веб приложение на Java (простой сайт)(2018)-->]( https://www.youtube.com/watch?v=jH17YkBTpI4&feature=youtu.be )
### ---Lessons---
+ [Spring Boot + Thymeleaf CRUD Example-->]( https://www.dariawan.com/tutorials/spring/spring-boot-thymeleaf-crud-example/ )
+ [Cascade Types (пример на Hibernate и Spring Boot)-->]( https://sysout.ru/tipy-cascade-primer-na-hibernate-i-spring-boot/ )
+ [Spring Boot + Spring MVC + Role Based Spring Security + JPA + Thymeleaf + MySQL Tutorial(2019)-->]( https://www.javaguides.net/2018/09/spring-boot-spring-mvc-role-based-spring-security-jpa-thymeleaf-mysql-tutorial.html )
+ [Spring Boot CRUD Application with Thymeleaf-->]( https://www.baeldung.com/spring-boot-crud-thymeleaf )
+ [Стоит ли использовать Spring Boot в вашем следующем проекте?(2014)-->]( https://habr.com/ru/post/244531/ )
+ [Из резюме джуна: Spring Boot — «волшебный» фреймворк Java(2020)-->]( https://javarush.ru/groups/posts/2930-iz-rezjume-dzhuna-spring-boot--volshebnihy-freymvork-java )
+ [Завоевание Spring Boot(2018)-->]( https://javarush.ru/groups/posts/497-zavoevanie-spring-boot )
+ [Руководство Spring Boot для начинающих-->]( https://o7planning.org/ru/11267/spring-boot-tutorial-for-beginners )
+ [Знакомство со Spring Boot-->]( https://topjava.ru/blog/introducing-spring-boot )
### ---Forum---























+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

[к оглавлению](#spring)
