[Java Tutorials](README.md)

# Hibernate

## Framework Hibernate

### Общие вопросы:
+ [Что такое JPA?](#Что-такое-JPA)
+ [Что такое ORM?](#Что-такое-ORM)
+ [Что такое Hibernate?](#Что-такое-Hibernate)
+ [В чем разница между JPA и Hibernate? Как связаны все эти понятия?](#В-чем-разница-между-JPA-и-Hibernate-Как-связаны-все-эти-понятия)
+ [Назовите интерфейсы Hibernate?](#Назовите-интерфейсы-Hibernate)
+ [Чем HQL отличается от SQL?](#Чем-HQL-отличается-от-SQL)
+ [Какие можно устанавливать параметры в hbm2ddl?](#Какие-можно-устанавливать-параметры-в-hbm2ddl)
+ [Можно ли использовать JPA c noSQl базами?](#Можно-ли-использовать-JPA-c-noSQl-базами)



### Сложные структуры JPA:



### Основные операции с Entity:
+ [Какие требования JPA к Entity классам вы можете перечислить?](#Какие-требования-JPA-к-Entity-классам-вы-можете-перечислить)
+ [Что такое EntityManager и какие основные его функции вы можете перечислить?](#Что-такое-EntityManager-и-какие-основные-его-функции-вы-можете-перечислить)
+ [Какие четыре статуса жизненного цикла Entity объекта (Entity Instance’s Life Cycle) вы можите перечислить?](#Какие-четыре-статуса-жизненного-цикла-Entity-объекта-вы-можите-перечислить)



### Аннотации JPA:
+ [Назовите аннотации Hibernate?](#Назовите-аннотации-Hibernate)



### Сложные вопросы JPA:

+ [ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ](#ССЫЛКИ-НА-ДОПОЛНИТЕЛЬНУЮ-ИНФУ)
+ [к оглавлению](#hibernate)



### Общие вопросы:

## Что такое JPA?
JPA (Java Persistence API) это спецификация Java EE и Java SE, описывающая систему управления сохранением java объектов в таблицы реляционных баз данных в удобном виде. Сама Java не содержит реализации JPA, однако есть существует много реализаций данной спецификации от разных компаний (открытых и нет). Это не единственный способ сохранения java объектов в базы данных (ORM систем), но один из самых популярных в Java мире. 

JPA состоит из 3 основных пунктов:
+ __API__ интерфейсы в пакете `javax.persistance`. Набор интерфейсов, которые позволяют взаимодействовать с ORM провайдером.
+ __JPQL__ объектный язык запросов. Очень похож на SQL, но запросы выполняются к объектам.
+ __Metadata__ аннотации над объектами. Набор аннотаций, которыми мы описываем метаданные отображения. Тогда уже JPA знает какой объект в какую таблицу нужно сохранить. Метаданные можно описывать 2 способами: XML-файлом или через аннотации.
+ [к оглавлению](#hibernate)

## Что такое ORM?
+ __ORM — Object-Relational Mapping или в переводе на русский объектно-реляционное отображение__. Это технология программирования, которая связывает базы данных с концепциями объектно-ориентированных языков программирования. Если упростить, то ORM это связь Java объектов и записей в БД.
+ ORM — это по сути концепция о том, что Java объект можно представить как данные в БД (и наоборот). Она нашла воплощение в виде спецификации JPA — Java Persistence API.
+ [к оглавлению](#hibernate)

## Что такое Hibernate?
__Hibernate__ —Это одна из наиболее популярных реализаций ORM-модели. Объектно-реляционная модель описывает отношения между программными объектами и записями в БД. Это  фреймворк библиотека, которая предназначена для задач объектно-реляционного отображения. Если простыми словами —  hibernate позволяет разработчику работать с базой данных не напрямую, как мы это делали с помощью библиотеки JDBC, а  с помощью представления таблиц баз данных в виде классов java.
[к оглавлению](#hibernate)

## В чем разница между JPA и Hibernate? Как связаны все эти понятия?
Hibernate одна из самых популярных открытых реализаций последней версии спецификации (JPA 2.1). Даже скорее самая популярная, почти стандарт де-факто. То есть JPA только описывает правила и API, а Hibernate реализует эти описания, впрочем у Hibernate (как и у многих других реализаций JPA) есть дополнительные возможности, не описанные в JPA (и не переносимые на другие реализации JPA).
[к оглавлению](#hibernate)

## Назовите интерфейсы Hibernate?
Существует пять ключевых интерфейсов которые используются в каждом приложении связанном с Hibernate:
+ Session interface;
+ SessionFactory interface;
+ Configuration interface;
+ Transaction interface;
+ Query and Criteria interfaces.

+ SessionFactory (org.hibernate.SessionFactory) – неизменяемый потокобезопасный объект с компилированным маппингом для одной базы данных. Необходимо инициализировать SessionFactory всего один раз. Экземпляр SessionFactory используется для получения объектов Session, которые используются для операций с базами данных.
+ Session (org.hibernate.Session) – однопоточный короткоживущий объект, который предоставляет связь между объектами приложения и базой данных. Он оборачивает JDBC java.sql.Connection и работает как фабрика для org.hibernate.Transaction. Разработчик должен открывать сессию по необходимости и закрывать ее сразу после использования. Экземпляр Session является интерфейсом между кодом в java приложении и hibernate framework и предоставляет методы для операций CRUD.
+ Transaction (org.hibernate.Transaction) – однопоточный короткоживущий объект, используемый для атомарных операций. Это абстракция приложения от основных JDBC или JTA транзакций. org.hibernate.Session может занимать несколько org.hibernate.Transaction в определенных случаях.
[к оглавлению](#hibernate)

## Чем HQL отличается от SQL?
__HQL (Hibernate Query Language)__ – это объекто-ориентированный язык запросов, который очень похож на SQL. Главное различие языков HQL и SQL связано с тем, что SQL формирует запросы из наименований таблиц в базе данных и их столбцов, а HQL работает с сущностями (классами) и их полями (аттрибутами класса).

Hibernate транслирует HQL–запросы в понятные для БД SQL–запросы, которые и выполняют необходимые действия в БД.

#### [Язык запросов HQL-->]( http://java-online.ru/hibernate-hql.xhtml )
[к оглавлению](#hibernate)

## Какие можно устанавливать параметры в hbm2ddl?
hibernate.hbm2ddl.auto Автоматически проверяет или экспортирует DDL схемы в базу данных при создании SessionFactory. С помощью create-drop схема базы данных будет удалена, когда SessionFactory будет закрыт явно.

Итак, список возможных вариантов:
+ __validate__ : проверяет схему, не вносит изменений в базу данных.
+ __update__ : обновить схему.
+ __create__ : создает схему, уничтожая предыдущие данные.
+ __create-drop__ : удалить схему при явном закрытии SessionFactory, обычно при остановке приложения.
+ __none__ - действие не выполняется. Схема не будет сгенерирована.
+ __create-only__ - Схема базы данных будет сгенерирована.
+ __drop__ - Схема базы данных будет удалена и впоследствии создана.
[к оглавлению](#hibernate)

## Можно ли использовать JPA c noSQl базами?
Вообще, спецификация JPA говорит только о отображении java объектов в таблицы реляционных баз данных, но при этом существует ряд реализаций данного стандарта для noSql баз данных: Kundera, DataNucleus, ObjectDB и ряд других. Естественно, при это не все специфичные для реляционных баз данных особенности спецификации переносятся при этом на nosql базы полностью.
[к оглавлению](#hibernate)

### Сложные структуры JPA:



### Основные операции с Entity:

## Какие требования JPA к Entity классам вы можете перечислить?
+ 1- Entity класс должен быть отмечен аннотацией Entity или описан в XML файле конфигурации JPA.
+ 2- Entity класс должен содержать public или protected конструктор без аргументов (он также может иметь конструкторы с аргументами).
+ 3- Entity класс должен быть классом верхнего уровня (top-level class).
+ 4- Entity класс не может быть enum или интерфейсом.
+ 5- Entity класс не может быть финальным классом (final class).
+ 6- Entity класс не может содержать финальные поля или методы, если они участвуют в маппинге (persistent final methods or persistent final instance variables).
+ 7- Если объект Entity класса будет передаваться по значению как отдельный объект (detached object), например через удаленный интерфейс (through a remote interface), он так же должен реализовывать Serializable интерфейс.
+ 8- Поля Entity класс должны быть напрямую доступны только методам самого Entity класса и не должны быть напрямую доступны другим классам, использующим этот Entity. Такие классы должны обращаться только к методам (getter/setter методам или другим методам бизнес-логики в Entity классе).
+ 9- Enity класс должен содержать первичный ключ, то есть атрибут или группу атрибутов которые уникально определяют запись этого Enity класса в базе данных.

[к оглавлению](#hibernate)

## Что такое EntityManager и какие основные его функции вы можете перечислить?
__EntityManager__ это интерфейс, который описывает API для всех основных операций над Enitity, получение данных и других сущностей JPA. По сути главный API для работы с JPA. Основные операции:
+ 1- Для операций над Entity: persist (добавление Entity под управление JPA), merge (обновление), remove (удаления), refresh (обновление данных), detach (удаление из управление JPA), lock (блокирование Enity от изменений в других thread),
+ 2- Получение данных: find (поиск и получение Entity), createQuery, createNamedQuery, createNativeQuery, contains, createNamedStoredProcedureQuery, createStoredProcedureQuery
+ 3- Получение других сущностей JPA: getTransaction, getEntityManagerFactory, getCriteriaBuilder, getMetamodel, getDelegate
+ 4- Работа с EntityGraph: createEntityGraph, getEntityGraph
+ 5- Общие операции над EntityManager или всеми Entities: close, isOpen, getProperties, setProperty, clear

[к оглавлению](#hibernate)

## Какие четыре статуса жизненного цикла Entity объекта вы можите перечислить?
У Entity объекта существует четыре статуса жизненного цикла: new, managed, detached, или removed. Их описание
+ 1- __new__ — объект создан, но при этом ещё не имеет сгенерированных первичных ключей и пока ещё не сохранен в базе данных.
+ 2- __managed__ — объект создан, управляется JPA, имеет сгенерированные первичные ключи.
+ 3- __detached__ — объект был создан, но не управляется (или больше не управляется) JPA.
+ 4- __removed__ — объект создан, управляется JPA, но будет удален после commit'a транзакции.

[к оглавлению](#hibernate)



### Аннотации JPA:
## Назовите аннотации Hibernate?
Рассмотрим аннотации, которые используются в стандарте JPA и в различных фреймворках вроде Hibernate.
+ @Entity	javax.persistence.Entity   – Указывает, что данный бин (класс) является сущностью.
+ @Table	javax.persistence.Table   – указывает на имя таблицы, которая будет отображаться в этой сущности.
+ @Column	javax.persistence.Table  – указывает на имя колонки, которая отображается в свойство сущности.
+ @Id	javax.persistence.Id   – id колонки
+ @GeneratedValue	javax.persistence.GeneratedValue   – указывает, что данное свойство будет создаваться согласно указанной стратегии
+ @Version	javax.persistence.Version   – управление версией в записи сущности. При изменении записи увеличится на 1.
+ @OrderBy	javax.persistence.OrderBy   – указание сортировки. В примере множество кошек будет отсортировано по имени по возрастанию
+ @Transient	javax.persistence.Transient   – указывает, что свойство не нужно записывать. Значения под этой аннотацией не записываются в базу данных (так же не участвуют в сериализации). static и final переменные экземпляра всегда transient.
+ @Lob	javax.persistence.Lob   – указание на большие объекты.
+ @PersistenceContext	javax.persistence.PersistenceContext   – указывает на зависимость EntityManager в контейнере
+ @Temporal	javax.persistence.TemporalType   – применяется к полям или свойствам с типом java.util.Date и java.util.Calendar. Например, если в БД время сохраняется как sql.Date, то чтобы использовать дату из java.util.Date указываем эту аннотацию.
+ @Embedded	javax.persistence.Embedded   – Определяет класс, экземпляры которого хранятся как неотъемлемая часть исходного объекта. Каждый из @Embedded экземпляров сопоставляется с таблицей базы данных сущности.

Аннотации для связи ассоциаций
+ @OneToOne	javax.persistence.OneToOne
+ @ManyToOne	javax.persistence.ManyToOne
+ @OneToMany	javax.persistence.OneToMany
+ @ManyToMany	javax.persistence.ManyToMany
+ @PrimaryKeyJoinColumn	javax.persistence.PrimaryKeyJoinColumn
+ @JoinColumn	javax.persistence.PrimaryKeyJoinColumn
+ @JoinTable	javax.persistence.JoinTable
+ @MapsId	javax.persistence.MapsId

Аннотации наследования
+ @Inheritance	javax.persistence.Inheritance
+ @DiscriminatorColumn	javax.persistence.DiscriminatorColumn
+ @DiscriminatorValue	javax.persistence.DiscriminatorValue

Аннотации запросов
+ @NamedQueries	javax.persistence.NamedQueries
+ @NamedQuery	javax.persistence.NamedQuery
+ @SqlResultSetMapping	javax.persistence.SqlResultSetMapping
+ @EntityResult	javax.persistence.EntityResult

Аннотации Hibernate
+ @Audited	org.hibernate.envers.Audited
+ @NotAudited	org.hibernate.envers.NotAudited
+ @Type	org.hibernate.annotations.Type

#### [Аннотации Java для работы с базой данных-->]( https://javastudy.ru/spring-data-jpa/annotation-persistence/ )

[к оглавлению](#hibernate)



### Сложные вопросы JPA:









## ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ

### ---Info---
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Package javax.persistence-->]( https://docs.oracle.com/javaee/7/api/javax/persistence/package-summary.html )
#### [Hibernate.org-->]( https://hibernate.org/orm/ )

### ---Video---
#### [YouTube/kuidreS/Hibernate - немного теории-->]( https://www.youtube.com/watch?v=HS7qJ4SRznM )
#### [YouTube/kuidreS/Урок 4 - Hibernate XML mapping-->]( https://www.youtube.com/watch?v=HUBuijE_Jg0 )
#### [YouTube/kuidreS/Урок 5 - Hibernate annotation mapping-->]( https://www.youtube.com/watch?v=qnZnu0dR36o&t=2s )
#### [YouTube/kuidreS/Урок 6 - содание DAO и Service слоев (Hibernate annotations, H2)-->]( https://www.youtube.com/watch?v=cCklIY78tc0 )
#### [YouTube/Java Vision/Java Hibernate часть 1-->](https://www.youtube.com/watch?v=Qt7HwPfwEKM )
#### [YouTube/Java Vision/Java Hibernate часть 2 Many To One-->]( https://www.youtube.com/watch?v=XcjE5dS21uE )
#### [YouTube/Java Vision/Java Hibernate часть 3 One To Many-->]( https://www.youtube.com/watch?v=R_j5mXF-Fe4 )
#### [YouTube/Java Vision/Java Hibernate часть 4 Many To Many-->]( https://www.youtube.com/watch?v=VQPoe2OVghQ )
#### [YouTube/JUG .ru/Вячеслав Круглов — Введение в Hibernate: что, зачем, и где стандартные ловушки-->]( https://www.youtube.com/watch?v=C-wEZjEOhWc )
#### [YouTube/LessonFirst/Java hibernate: Настройка конфигов, урок 1!-->]( https://www.youtube.com/watch?v=1qYOxJ-OEWs&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0 )
#### [YouTube/LessonFirst/Java hibernate: xml маппинг, урок 2!-->]( https://www.youtube.com/watch?v=cnw5PHdsDtQ&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=2 )
#### [YouTube/LessonFirst/Java hibernate: XML мапинг, связь многие к одному, урок 3!-->]( https://www.youtube.com/watch?v=hhO6JgfHitU&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=3 )
#### [YouTube/LessonFirst/Java hibernate: XML мапинг, связь один к одному, урок 4!-->]( https://www.youtube.com/watch?v=FsBGZW6qJXM&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=4 )
#### [YouTube/LessonFirst/Java hibernate: XML мапинг, связь многие ко многим, урок 5!-->]( https://www.youtube.com/watch?v=rUER9XgNuy4&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=5 )
#### [YouTube/LessonFirst/Java hibernate: Введение в JPA, урок 6!-->]( https://www.youtube.com/watch?v=-Ld6xgd2K4k&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=6 )
#### [YouTube/LessonFirst/Java hibernate: JPA связь многие к одному, урок 7!-->]( https://www.youtube.com/watch?v=wfnbF7aELUk&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=7)
#### [YouTube/LessonFirst/Java hibernate: JPA связь один к одному, урок 8!-->]( https://www.youtube.com/watch?v=JJBrkkKuC2M&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=8 )
#### [YouTube/LessonFirst/Java hibernate: JPA связь многие ко многим, урок 9!-->]( https://www.youtube.com/watch?v=h3PHEUuOmZA&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=9 )
#### [YouTube/LessonFirst/Java hibernate: JPA Пример использования мапинга, урок 10!-->]( https://www.youtube.com/watch?v=3WjcQiemvWM&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=10 )
#### [YouTube/LessonFirst/Java hibernate: Транзакции, урок 11!-->]( https://www.youtube.com/watch?v=j2Eky9D9RkA&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=11 )
#### [YouTube/LessonFirst/Java hibernate: SQL запросы, урок 12!-->]( https://www.youtube.com/watch?v=p1B4pz0G19o&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=12 )
#### [YouTube/LessonFirst/Java hibernate: HQL запросы, урок 13!-->]( https://www.youtube.com/watch?v=IJMgD1MNdNM&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=13 )
#### [YouTube/LessonFirst/Java hibernate: Criteria запросы, урок 14!-->]( https://www.youtube.com/watch?v=oJi4ljPJ6IA&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=14 )
#### [YouTube/LessonFirst/Java hibernate: Валидация, урок 15!-->]( https://www.youtube.com/watch?v=Pg96t-T1G-E&list=PLi3gxGWPyGGQsEZyjQNPoUEHwNtxiMf-0&index=15 )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [YouTube/GeekBrains/Изучите Hibernate на практике GeekBrains-->]( https://www.youtube.com/watch?v=4CLlk9EeUeo )
#### [YouTube/D2D/Курс Java для начинающих. Занятие №9. ORM JPA Hibernate-->]( https://www.youtube.com/watch?v=u4GSk3GVZNw )
#### [YouTube/luv2code/Hibernate Tutorial #1 - Hibernate Overview(ENG)-->]( https://www.youtube.com/watch?v=0hm3QidFwYY&list=PLEAQNNR8IlB7fNkRsUgzrR346i-UqE5CG&index=1 )

### ---Lessons---
#### [Hibernate. Основные принципы работы с сессиями и транзакциями-->]( https://habr.com/ru/post/271115/ )
#### [Ваше первое приложение на Hibernate-->]( https://javarush.ru/groups/posts/hibernate-java )
#### [Аннотации. Часть первая, немного скучная-->]( https://javarush.ru/groups/posts/500-annotacii-chastjh-pervaja-nemnogo-skuchnaja )
#### [Аннотации. Часть вторая. Lombok-->]( https://javarush.ru/groups/posts/518-annotacii-chastjh-vtoraja-lombok )
#### [Hibernate — Краткое руководство-->]( https://coderlessons.com/tutorials/java-tekhnologii/vyuchit-hibernate/hibernate-kratkoe-rukovodstvo )
#### [Руководство Java Hibernate для начинающих-->]( https://o7planning.org/ru/10201/java-hibernate-tutorial-for-beginners#a77362 )
#### [Java Query примеры использования-->]( https://java.hotexamples.com/ru/examples/javax.persistence/Query/-/java-query-class-examples.html )
#### [QueryDSL: Предикаты-->]( https://habr.com/ru/post/344450/ )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

### ---Forum---
#### [Hibernate 5 Java Configuration Example-->]( https://dzone.com/articles/hibernate-5-java-configuration-example )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )
#### [Название-->]( Ссылка )

[к оглавлению](#hibernate)
