[Java Tutorials](README.md)

# Spring

## Spring Core
+ [My summary of spring studies](#My-summary-of-spring-studies)
+ [Что такое Spring? Чем фреймворк отличается от библиотеки?](#Что-такое-Spring-Чем-фреймворк-отличается-от-библиотеки)
+ [Что такое бины?](#Что-такое-бины)
+ [Назовите способы создания бинов?](#Назовите-способы-создания-бинов)
+ [Виды бинов? Скоупы бинов? Какой по-умолчанию?](#Виды-бинов-Скоупы-бинов-Какой-по-умолчанию)
+ [Чем бин отличается от POJO-класса?](#Чем-бин-отличается-от-POJO-класса)
+ [Что такое Inversion of Control и как Spring реализует этот принцип?](#Что-такое-Inversion-of-Control-и-как-Spring-реализует-этот-принцип)
+ [Что такое контекст Spring и как его создать?](#Что-такое-контекст-Spring-и-как-его-создать)
+ [Как можно связать бины?](#Как-можно-связать-бины)
+ [@Autowired, где можно ставить и какие есть отличия?](#Autowired-где-можно-ставить-и-какие-есть-отличия)
+ [Опишите поведение аннотации @Autowired](#Опишите-поведение-аннотации-Autowired)
+ [Что такое Dependency Injection? Чем отличается от композиции?](#Что-такое-Dependency-Injection-Чем-отличается-от-композиции)
+ [Какие бины будут использоваться для настройки приложения?](#Какие-бины-будут-использоваться-для-настройки-приложения)
+ [Принципы работы Spring.](#принципы-работы-Spring)
+ [Жизненный цикл Бина.](#Жизненный-цикл-Бина)
+ [Основные паттерны Spring.](#Основные-паттерны-Spring)
+ [Рассказать про Singleton, как реализуется без Спринга?](#Рассказать-про-Singleton-как-реализуется-без-Спринга)


## Spring MVC
+ [Как получить данные из файла .property?](#Как-получить-данные-из-файла-property)
+ [Как запустить Спринг-приложение из-под сервера Tomcat?](#Как-запустить-Спринг-приложение-из-под-сервера-Tomcat)
+ [Что такое Artifacts?](#Что-такое-Artifacts)
+ [В чем отличие артефакта war от war exploded?](#В-чем-отличие-артефакта-war-от-war-exploded)
+ [Какая разница между аннотациями @Component, @Repository и @Service в Spring?](#Какая-разница-между-аннотациями-Component-Repository-и-Service-в-Spring)
+ [Как выглядит структура MVC-приложения?](#Как-выглядит-структура-MVC-приложения)
+ [Какая основная зависимость фреймворка Спринг? Почему во многих сборках она не указывается явно?](#Какая-основная-зависимость-фреймворка-Спринг-Почему-во-многих-сборках-она-не-указывается-явно)
+ ???[Чем контроллер отличается от сервлета?](#Чем-контроллер-отличается-от-сервлета)
+ ???[Как вернуть страницу в контроллере? Как вернуть данные?](#Как-вернуть-страницу-в-контроллере-Как-вернуть-данные)
+ [Как интегрировать Hibernate и Spring?](#Как-интегрировать-Hibernate-и-Spring)



## Spring Security
+ [Как подключить Spring Security к проекту?](#Как-подключить-Spring-Security-к-проекту)
+ [Как мы можем добавить секьюрность к контроллеру? (минимум 2 способа).](#Как-мы-можем-добавить-секьюрность-к-контроллеру-минимум-2-способа)
+ [Что будет являться эквивалентом пользователя и роли в приложении со Spring Security?](#Что-будет-являться-эквивалентом-пользователя-и-роли-в-приложении-со-Spring-Security)
+ [Какие варианты хранения информации о пользователях вы знаете?](#Какие-варианты-хранения-информации-о-пользователях-вы-знаете)
+ [Аутентификация и Авторизация - в чём разница?](#Аутентификация-и-Авторизация-в-чём-разница)






+ [к оглавлению](#spring)





# Spring Core

## My summary of spring studies

__Configuration using annotations:__
### Spring Core
+ @Component("/id/") - Indicates the desired class when scanning
+ @Autowired - Needed for dependency injection
+ @Qualifier("/dog/") - Used to specify which bean to embed dependencies in
+ @Value("/Sidorov/") - Used for embedding values in fields
+ @Scope("prototype") - Used to specify the scope of the bean
+ @PostConstruct - Used to specify the init-method
+ @PreDestroy - Used to specify the destroy-method 
+ @Comfiguration - Indicates that this class is a configuration
+ @ComponentScan("/web/") - Shows which package to scan for beans and different annotations
+ @EnableAutoConfiguration - 
+ @Bean - To create a bean manually
+ @PropertySource("classpath:myApp.properties") - Shows to the property file where we can use values for fields
+ @Order(2) - Used for ordering elements
### Spring AOP
+ @EnableAspectJAutoProxy - Allows us to use Spring AOP Proxy behind the scenes
+ @Aspect - Indicates that this is not a regular class, but an Aspect
+ @Before("execution(public void getBook())") - Executed before the method with the main logic
+ @AfterReturning - It is executed only after the normal completion of the method with the main logic, but before assigning the result of this method to any variable
+ @AfterThrowing - Executed after the end of the method with the main logic only if an exception was thrown
+ @After - Always executed after the end of the method with the main logic
+ @Around - Executed before and after the method with the main logic
+ @Pointcut("pointcut_expression") - Ad Pointcut
### Hibernate
+ @Entity - An annotation that reflects information from a specific table in the database
+ @Table(name="employees") - Indicates that the class displays a specific table
+ @Column(name="id") - Indicates which column from the table we are binding the class field to
+ @Id - Indicates that in the table, the column associated with this field is Primary Key
+ @GeneratedValue(strategy = GenerationType.IDENTITY) - Describes a strategy for generating values for a column with Primary Key
+ @OneToOne - Indicates the type of relationship between objects
+ @OneToMany - Indicates the type of relationship between objects
+ @ManyToOne - Indicates the type of relationship between objects
+ @ManyToMany - Indicates the type of relationship between objects
+ @JoinColumn(name="details_id") - Points to a column that links to another object. Will always refer to the field with the Foreign Key
+ @JoinTable(name="child_section", joinColumns = @JoinColumn(name="child_id"), inverseJoinColumns = @JoinColumn(name="section_id")) - Enter the name of the table that performs the role of Join Table
### Spring MVC
+ @Controller - Specialized @Component
+ @Repository - Specialized @Component. This annotation is used for the DAO 
+ @Service - Specialized @Component. Marks a class that contains business logic. Service is the connecting link between the Controller and the DAO
+ @RestController - This is the Controller that manages REST requests and responses
+ @RequestMapping("/") - Binds the URL to the controller method
+ @GetMapping - Binds an HTTP request that uses the HTTP GET method to the Controller method
+ @PostMapping - Binds an HTTP request that uses the HTTP POST method to the Controller method
+ @PutMapping - Binds an HTTP request that uses the HTTP PUT method to the Controller method
+ @DeleteMapping - Binds an HTTP request that uses the HTTP DELETE method to the Controller method
+ @RequestParam("employeName") - Allows us to associate a form field with a method parameter from the controller
+ @RequestBody - Binds the HTTP method body to the Controller method parameter
+ @PathVariable int id - Used to get the value of a variable from the request address
+ @ModelAttribute("employee") - When it is in a controller method parameter, it gives access to a specific attribute of the model
+ @Transactional - Spring takes responsibility for opening and closing transactions
+ @ExceptionHandler - The method responsible for exception handling is marked
+ @ControllerAdvice - A class that provides the Global Exception Handler functionality is marked

### Spring Boot
+ @SpringBootAplication - Replaces the following annotations @Comfiguration/ @EnableAutoConfiguration/ @ComponentScan


Spring Core

+ __Spring Bean__ - This is an object that is created and managed by Spring Container.
+ __Application Context__ - it consists of Spring Container.

__Main function Spring Container:__ 
__1. IoC__ Inversion of control. The creation and management of objects
__2. DI__ Dependency Injection.

__Configuration methods Spring Container:__ 
1. XML file
2. Annotations + XML file
3. Java code

__Ways to Dependency Injection(DI):__
1. Using the constructor
2. Using setters
3. Autowiring

__Bean scope:__
+ Bean lifecycle
+ Possible number of beans to create

__Varieties of bean scope:__
+ singletone (default)
+ prototype (statefull)
+ request
+ session
+ global-session

__Bean lifecycle:__
1. App startup
2. Start of work Spring Container
3. Creating a bean
4. Dependency Injection
5. `Init-method`(If they have)
6. The Bean is ready to use
7. Our use of this Bean
8. End of work Spring Container
9. `Destroy-method`(If they have)
10. Stopping the app

__Dependency injection is performed:__
1. using the constructor
2. using the setter
3. using the field

__The process of dependency injection when using an @Autowired annotation:__
1. Scanning the package, searching for classes with the @Component annotation.
2. If the @Autowired annotation is present, the search for a suitable bean type begins.
3. What happens next dependency injection.

Spring AOP

+ __Advice__ - A method that is contained in Aspect and contains end-to-end logic.
+ __Pointcut__- Expression describing where Advice should be applied.
+ __Join Point__ - The point in the program when to apply Advice. The intersection point of a method with business logic and a method with service functionality.
+ __ProceedingJoinPoint__ - Required for calling the target method

__Advice types in AOP__
+ Before - Executed before the method with the main logic
+ After returning - It is executed only after the normal completion of the method with the main logic, but before assigning the result of this method to any variable
+ After throwing - Executed after the end of the method with the main logic only if an exception was thrown
+ After/After finally - Always executed after the end of the method with the main logic
+ Around - Executed before and after the method with the main logic

__Pointcut template__
__execution(__ modifiers-pattern? __return-type-pattern__ declaring-type-pattern? 
__method-name-pattern(parameters-pattern)__ throws-pattern? __)__

Hibernate

__Loading type:__
1. fetch = FetchType.EAGER - When using the related entities are loaded at once together with the download of the primary entity
2. fetch = FetchType.LAZY - When using it, related entities ARE not loaded immediately when the main entity is loaded. Related entities are loaded only when they are accessed for the first time

__Default Fetch type:__
+ One-to-One --> __Eager__
+ One-to-Many --> __Lazy__
+ Many-to-One --> __Eager__
+ Many-to-Many --> __Lazy__

+ [к оглавлению](#spring)

## Что такое Spring? Чем фреймворк отличается от библиотеки?
Spring Framework - представляет собой просто контейнер внедрения зависимостей, с несколькими удобными слоями (например: доступ к базе данных, прокси, аспектно-ориентированное программирование, RPC, веб-инфраструктура MVC). Это все позволяет вам быстрее и удобнее создавать Java-приложения.


«Фреймворк» отличается от понятия библиотеки тем, что библиотека может быть использована в программном продукте просто как набор подпрограмм близкой функциональности, не влияя на архитектуру программного продукта и не накладывая на неё никаких ограничений. В то время как «фреймворк» диктует правила построения архитектуры приложения, задавая на начальном этапе разработки поведение по умолчанию — «каркас», который нужно будет расширять и изменять, согласно указанным требованиям.

Также, в отличие от библиотеки, которая объединяет в себе набор близкой функциональности, — «фреймворк» может содержать в себе большое число разных по тематике библиотек.

Другим ключевым отличием «фреймворка» от библиотеки может быть инверсия управления: пользовательский код вызывает функции библиотеки (или классы) и получает управление после вызова. Во «фреймворке» пользовательский код может реализовывать конкретное поведение, встраиваемое в более общий — «абстрактный» код фреймворка. При этом «фреймворк» вызывает функции (классы) пользовательского кода.
+ [к оглавлению](#spring)


## Что такое бины?
Начнем срывать покровы с самых базовых понятий Spring. Бин (bean) — это не что иное, как самый обычный объект. Разница лишь в том, что бинами принято называть те объекты, которые управляются Spring-ом и живут внутри его DI-контейнера. Бином является почти все в Spring — сервисы, контроллеры, репозитории, по сути все приложение состоит из набора бинов. Их можно регистрировать, получать в качестве зависимостей, проксировать, мокать и т.п.
+ [к оглавлению](#spring)


## Назовите способы создания бинов?
__Существует 4 способа создания бинов:__
+ xml - старый способ, как преимущество - централизованная конфигурация контекста
+ аннотации - простота и удобство, как недостаток - децентрализованная конфигурация
+ Java конфигурация - пока лучший способ.
+ Groovy - заменит и java и xml, но пока он не достаточно хорош.

+ __XML__

Исторически конфигурирование контекста c использованием XML было первым методом конфигурирования, появившемся в Spring.
Конфигурирование с помощью XML заключается в создании xml файла (традиционно носящего названия вида «context.xml», «applicationContext.xml» и т.д.), описывающего Spring beans, процесс их создания и взаимосвязи между ними. 
Не использует аннотаций.
```java
    <bean id="coin" class="stas.paliutin.spring.CoinImpl">
        <constructor-arg type="java.util.Random">
            <bean class="java.util.Random"/>
        </constructor-arg>
    </bean>
```
Вначале мы определили бин «coin», передав ему в конструктор внутренний анонимный бин, созданный из java.util.Random. Связывание было проведено по типу аргумента, а передаваемый в конструктор бин был определён на месте.

+ __Аннотации__
```java
ApplicationContext context = 
	new AnnotationConfigApplicationContext("where.is.entities");
```
Сначала мы создаем объект контекста, и в конструкторе указываем ему имя пакета, которое надо сканировать на наличие в нем бинов.
Второй способ сделать это, через указание аннотации @ComponentScan(“...”) вместе с @Configuration. 
```java
@Configuration
@ComponentScan("where.is.entities")
public class WebConfig {
    private static ApplicationContext applicationContext;

    public WebConfig(ApplicationContext applicationContext) {
        this.applicationContext = applicationContext;
    }
```
То-есть, спринг пройдется по этому пакету и попробует найти такие классы, которые отмечены специальными аннотациями, дающими спрингу понять, что это — бин. После чего он создает объекты этих классов и помещает их себе в контекст.
Сами бины для сканирования помечаются через аннотации @Component и все остальные аннотации, которые наследуются от этой. Например, @Controller, @RestController, @Service, @Repository и другие.
Имя бина будет именем класса с маленькой буквы. Либо можно специально указать в () аннотации.
```java
@Component(“myBean”);
```
Суть: Пишете ваши классы, отмечаете их нужными аннотациями, и указываете спрингу пакет с вашими классами, по которому он идет, ищет аннотации и создает объекты таких классов.

+ __JAVA конфигурация__

Чтобы создать класс с конфигурацией на основе Java-кода, нужно аннотировать его с помощью
@Configuration.
Spring вызывает в конфигурационных классах методы с аннотацией @Bean. Объекты, возвращённые этими методами, регистрируются как Spring бины. Названия бинов соответствуют названиям методов, которые их порождают.
```java
    @Bean
    public Cat cat() {
        return new Cat(“Meoy”);
    }
```
Java конфигурация выглядит наилучшим образом, если сравнивать её достоинства и недостатки. Это и централизованность как в xml; и безопасность типов; и простой рефакторинг; и отсутствия spring специфичных вещей в коде; и возможность выполнения каких-либо действий на этапе конфигурации. К недостаткам, пожалуй, относится необходимость ручного создания бинов и необходимость пересборки для переконфигурации приложения.

Важно и название класса конфигурации: несмотря на искушение назвать конфигурационный класс Context, делать этого не следует. Дело в том, что Spring создаст бин и из этого класса, а в качестве имени использует имя класса. А имя «Context» уже занято самим Spring.

+ __Groovy__

Поддержка Groovy скриптов и специального beans DSL появилась в 4 версии Spring как попытка сделать конфигурацию вообще без недостатков. Groovy конфигурация должна объединить в себе достоинства XML конфигурации и Java конфигурации, оставаясь дружественной к аннотациям.
К достоинствам groovy конфигурации можно отнести всё хорошее, что есть в XML и Java подходах: централизованное описание приложения, которое может хранится отдельно от кода, позволяя менять структуру приложения без пересборки (а в перспективе без перезапуска); использование стороннего кода в качестве Spring beans; возможность сохранить код чистым от Spring аннотаций; безопасность типов и простота рефакторинга; выполнение кода на этапе конфигурирования. Однако поддержка groovy конфигурации ещё недостаточно доработана и не все возможности, достижимые с помощью xml/java, доступны с groovy.
+ [к оглавлению](#spring)


## Виды бинов? Скоупы бинов? Какой по-умолчанию?
Бины можно классифицировать по функциональной роли и по “Скоупу” (во многих источниках “области видимости”)
По функциональному назначение бины могут аннотироваться разным способом (Стереотипы):
+ __@Component__ - бин общего назначения
+ __@Controller__ - контроллер в архитектуре MVC
+ __@Service__ - сервисный слой
+ __@Repository__ - дао слой

__Scope бинов__
Область видимости указывается с помощью аннотации @Scope на @Bean методах или .
+ __singleton__ 
Определяет один единственный бин для каждого контейнера Spring IoC (используется по умолчанию).
+ __prototype__
Позволяет иметь любое количество экземпляров бина.
+ __request__
Создаётся один экземпляр бина на каждый HTTP запрос. Касается исключительно ApplicationContext.
+ __session__
Создаётся один экземпляр бина на каждую HTTP сессию. Касается исключительно ApplicationContext.
+ __global-session__
Создаётся один экземпляр бина на каждую глобальную HTTP сессию. Касается исключительно ApplicationContext.

По умолчанию бину присваивается Скоуп singleton.
+ [к оглавлению](#spring)



## Чем бин отличается от POJO-класса?
__POJO (англ. Plain Old Java Object)__ — «старый добрый Java-объект», простой Java-объект, не унаследованный от какого-то специфического объекта и не реализующий никаких служебных интерфейсов сверх тех, которые нужны для бизнес-модели.

Все JavaBeans - это POJO, но не все POJO - это JavaBeans.

JavaBean - это объект Java, который удовлетворяет определенным соглашениям о программном обеспечении:
+ 1 - класс JavaBean должен реализовывать либо Serializable, либо Externalizable;
+ 2 - класс JavaBean должен иметь открытый конструктор no-arg;
+ 3 - все свойства JavaBean должны иметь общедоступные методы setter и getter (в зависимости от ситуации);
+ 4 - все переменные экземпляра JavaBean должны быть частными.
+ [к оглавлению](#spring)

## Что такое Inversion of Control и как Spring реализует этот принцип?
__Inversion of Control (инверсия управления)__ — это некий абстрактный принцип, набор рекомендаций для написания слабо связанного кода. Суть которого в том, что каждый компонент системы должен быть как можно более изолированным от других, не полагаясь в своей работе на детали конкретной реализации других компонентов.
__Как Spring реализует этот принцип?__
Центральной частью Spring является контейнер Inversion of Control, который предоставляет средства конфигурирования и управления объектами Java с помощью рефлексии. Контейнер отвечает за управление жизненным циклом объекта: создание объектов, вызов методов инициализации и конфигурирование объектов путём связывания их между собой и т.д.

Объекты, создаваемые контейнером, также называются управляемыми объектами (beans). Обычно, конфигурирование контейнера, осуществляется путём внедрения аннотаций (начиная с 5 версии J2SE), но также, есть возможность, по старинке, загрузить XML-файлы, содержащие определение bean’ов и предоставляющие информацию, необходимую для создания bean’ов.

#### [Концепция Inversion of Control и основы Spring-->]( http://javatutor.net/articles/spring-basic-and-inversion-of-control )
#### [Инверсии зависимостей управления впрыском-->]( https://habr.com/ru/post/321344/ )
#### [Spring для домохозяек. Inversion of Control на практике.-->]( https://nikcode.blogspot.com/2011/09/spring-inversion-of-control.html )
+ [к оглавлению](#spring)

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
+ [к оглавлению](#spring)

## Как можно связать бины?
__Явное и неявное связывание__
+ __неявная инъекция зависимостей, также называемую autowiring.__ 
Чтобы выполнить инъекцию, такие фреймворки будут искать в контексте подходящего кандидата. И потерпят неудачу, если не найдут ни одного подходящего класса или более одного.
+ __явное внедрение зависимостей__
В этом случае разработчику необходимо сконфигурировать инъекцию путем явной привязки отношения между объектом и зависимостью.
+ [к оглавлению](#spring)


## @Autowired, где можно ставить и какие есть отличия?
Аннотация __@Autowired__ применяется для неявного внедрения зависимости. Размещение аннотации определяет тип DI. Возможны три способа размещения. Над полем, сеттером, конструктором.

Ниже перечислены типы DI, которые предоставляет Spring:
+ __Constructor DI (через конструктор)__
DI через конструктор считается самым лучшим способом, т.к. для него не надо использовать рефлексию, а также он не имеет недостатков DI через сеттер.
DI через конструктор может приводить к циклическим зависимостям. Чтобы этого избежать, можно использовать ленивую инициализацию бинов или DI через сеттер.

Так же к плюсам относится (+):
в любой момент времени вы всегда получите готовый к работе класс со всеми зависимостями;
данные классы можно просто тестировать как обычные Java-классы и без поднятия контекста для тестирования;
в unit-тестах вы не сможете забыть добавить какую-либо зависимость, так как она будет требоваться на уровне компиляции.

+ __Setter DI (через сеттер)__
- Этот подход не является хорошей идеей, так как нет причин, по которым зависимость должна меняться во время жизненного цикла внедряемого объекта. 
- до того момента, как Spring проставит все зависимости в бин, экземпляр класса находится в некорректном состоянии. И обращение к зависимостям может привести к NullPointerException. Для того, чтобы сделать какие-то действия после того, как все зависимости будут инъектированы, используют аннотацию @PostConstruct.
+  тестировать эти классы почти так же просто, как и в случае DI через параметры конструктора. Но в тестах очень легко забыть проставить зависимость, не вызвав свежедобавленный сеттер.

+ __Field DI (через поле)__
+ Простота и минимум кода.
- DI через поле не рекомендуется использовать, т.к. для этого применяется рефлексия, снижающая производительность.
- Также, данный класс нельзя просто протестировать, не поднимая Spring Context. 
+ [к оглавлению](#spring)


## Опишите поведение аннотации @Autowired
+ 1.Контейнер определяет тип объекта для внедрения
+ 2.Контейнер ищет бины в контексте(он же контейнер), которые соответствуют нужному типу
+ 3.Если есть несколько кандидатов, и один из них помечен как @Primary, то внедряется он
+ 4.Если используется аннотации @Autowire + Qualifier, то контейнер будет использовать информацию из @Qualifier, чтобы понять, какой компонент внедрять
+ 5.В противном случае контейнер попытается внедрить компонент, основываясь на его имени или ID
+ 6.Если ни один из способов не сработал, то будет выброшено исключение

Контейнер обрабатывает DI с помощью AutowiredAnnotationBeanPostProcessor. В связи с этим, аннотация не может быть использована ни в одном BeanFactoryPP или BeanPP.

Если внедряемый объект массив, коллекция, или map с дженериком, то Spring внедрит все бины подходящие по типу в этот массив(или другую структуру данных). В случае с map ключом будет имя бина.
+ [к оглавлению](#spring)


## Что такое Dependency Injection? Чем отличается от композиции?
__Внедрение зависимостей__ — это специальный паттерн, который уменьшает связь между Spring компонентами. Таким образом, при применении DI, ваш код становится чище, проще, его становится легче понять и тестировать. 

Согласно паттерну DI, создание объектов для зависимостей переходит на фабрику или отдается третьей стороне. Это означает, что мы можем сосредоточиться на использовании этих объектов вместо их создания.

__Внедрение зависимостей (DI)__ - реализация принципа IoC — это стиль настройки объекта, при котором поля объекта задаются внешней сущностью. Другими словами, объекты настраиваются внешними объектами. 

Композиция - один из видов отношений классов в терминологии ООП. Таким образом DI также является и реализацией отношения - композиция.
+ [к оглавлению](#spring)


## Какие бины будут использоваться для настройки приложения?
Основными признаками и частями Java-конфигурации IoC контейнера являются классы с аннотацией `@Configuration` и методы с аннотацией `@Bean`. Аннотация `@Bean` используется для указания того, что метод создает, настраивает и инициализирует новый объект, управляемый Spring IoC контейнером. Такие методы можно использовать как в классах с аннотацией `@Configuration`, так и в классах с аннотацией `@Component`(или её наследниках). Класс с аннотацией `@Configuration` говорит о том, что он является источником определения бинов. 
+ [к оглавлению](#spring)


## Принципы работы Spring.
Спринг решает несколько проблем связанных с разработкой приложений. Ключевыми среди них являются:
+ __Создание и управление объектами (IoC)__
+ 1.Мы описываем объекты, которые необходимы для работы нашего приложения (которые должны создаваться при запуске приложения) в конфигурационном файле.
+ 2.Спринг сам создает эти объекты и берёт на себя управление этими объектами (их жизненный цикл и много другое, например Scope Singleton). 
+ 3.Объекты размещаются в специальном контейнере Spring Application Context. И предоставляет объекты из него, по необходимости.
+ 4.Спринг сам внедряет все необходимые зависимости в объекты, связывает объекты между собой (у объектов есть ссылка на другие нужные им объекты). Нам необходимо только описать эту связь. Спринг делает всё остальное. Это называется Dependency Injection (DI).

+ __Удобный и эффективный доступ к БД__
+ __Приложение сервер, в архитектуре клиент-сервер.__
+ __Настройка разграничения доступа к данным__
+ [к оглавлению](#spring)


## Жизненный цикл Бина.
__Жизненный цикл__ - время существования класса. Spring бины инициализируются при инициализации Spring контейнера и происходит внедрение всех зависимостей. Когда контейнер уничтожается, то уничтожается и всё содержимое. Если нам необходимо задать какое-либо действие при инициализации и уничтожении бина, то нужно воспользоваться методами `init()` и `destroy()`. Для этого можно использовать аннотации `@PostConstruct` и `@PreDestroy()`.
```java
@PostConstruct
public void init(){
    System.out.println(“Bean init method called”);
}

@PreDestroy
public void destroy(){
    System.out.println(“Bean destroy method called”);
}
```
Или через xml конфигурацию:
```
<bean name="myBean" class="ru.javastudy.spring.MyBean"
        init-method="init" destroy-method="destroy">
    <property name="someProp" ref="someProp"></property>
</bean>
```
Для prototype бинов, спринг не вызывает метод дестрой. Об этом должен заботиться разработчик сам.

__Рассмотрим жизненный цикл более подробно:__

Через следующие этапы проходит каждый отдельно взятый бин:
+ 1.Инстанцирование объекта. Техническое начало жизни бина, работа конструктора его класса;
+ 2.Установка свойств из конфигурации бина, внедрение зависимостей;
+ 3.Нотификация aware-интерфейсов. BeanNameAware, BeanFactoryAware и другие. Мы уже писали о таких интерфейсах ранее. Технически, выполняется системными подтипами BeanPostProcessor, и совпадает с шагом 4;
+ 4.Пре-инициализация – метод postProcessBeforeInitialization() интерфейса BeanPostProcessor;
+ 5.Инициализация. Разные способы применяются в таком порядке:
+ Метод бина с аннотацией @PostConstruct из стандарта JSR-250 (рекомендуемый способ);
+ Метод afterPropertiesSet() бина под интерфейсом InitializingBean;
+ Init-метод. Для отдельного бина его имя устанавливается в параметре определения initMethod. В xml-конфигурации можно установить для всех бинов сразу, с помощью default-init-method;
+ 6.Пост-инициализация – метод postProcessAfterInitialization() интерфейса BeanPostProcessor.

Когда IoC-контейнер завершает свою работу, мы можем кастомизировать этап штатного уничтожения бина. Как со всеми способами финализации в Java, при жестком выключении (kill -9) гарантии вызова этого этапа нет. Три альтернативных способа «деинициализации» вызываются в том же порядке, что симметричные им методы инициализации:

Метод с аннотацией `@PreDestroy`;
Метод с именем, которое указано в свойстве `destroyMethod` определния бина (или в глобальном `default-destroy-method`);
Метод `destroy()` интерфейса `DisposableBean`.

Не следует путать жизненный цикл отдельного бина с жизненным циклом контекста и этапами подготовки фабрик бинов.
+ [к оглавлению](#spring)


## Основные паттерны Spring.
Вот некоторые известные паттерны, используемые в Spring Framework:
+ Proxy (Заместитель)
+ Singleton (Одиночка)
+ Factory (Фабрика)
+ Template (Шаблон)
+ Model View Controller (Модель-Представление-Контроллер)
+ Front Controller (Контроллер запросов)
+ View Helper (Вспомогательный компонент представления)
+ Dependency injection и Inversion of control (IoC) (Внедрение зависимостей и инверсия управления)
+ Service Locator (Локатор служб)
+ Observer-Observable (Наблюдатель)
+ Context Object (Контекстный объект)

[Подробная статья-->](https://habr.com/ru/company/otus/blog/451516/)
+ [к оглавлению](#spring)


## Рассказать про Singleton, как реализуется без Спринга?
Просто реализовать (Singleton) — достаточно скрыть конструктор и предоставить статический создающий метод.
```java
public final class Singleton {
    private static Singleton instance;
    public String value;

    private Singleton(String value) {
        // Этот код эмулирует медленную инициализацию.
        // К паттерну отношения не имеет.
        try {
            Thread.sleep(1000);
        } catch (InterruptedException ex) {
            ex.printStackTrace();
        }
        this.value = value;
    }

    public static Singleton getInstance(String value) {
        if (instance == null) {
            instance = new Singleton(value);
        }
        return instance;
    }
}
```
+ [к оглавлению](#spring)








# Spring MVC

## Как получить данные из файла .property?
```java 
@Configuration
@PropertySource("classpath:/com/myco/app.properties")
public class AppConfig {

   @Autowired
   Environment env;

   @Bean
   public TestBean testBean() {
       TestBean testBean = new TestBean();
       testBean.setName(env.getProperty("testbean.name"));
       return testBean;
   }
}
```
В наших проектах использовали этот, но есть и другие способы
[-->](https://issue.life/questions/9259819)
PropertyPlaceholderConfigurer
PropertySource
ResourceBundleMessageSource
PropertiesFactoryBean
и др.
+ [к оглавлению](#spring)


## Как запустить Спринг-приложение из-под сервера Tomcat? 
В приложении нет метода main, его запуск происходит из-под Tomcat и для этого требуется отдельный класс AppInit, который ссылается на корневой конфигурационный файл и обозначает, на каком url будет находиться наше приложение.

Развертывание WAR на Tomcat
Чтобы развернуть и запустить наш файл WAR в Tomcat в виде сервиса, нам нужно выполнить следующее:

Скопировать наш WAR-файл из target/spring-app.war в
папку tomcat/webapps/
Перейти к http://localhost : 8080/spring-app/hello
+ [к оглавлению](#spring)


## Что такое Artifacts?
__Артефакт__ - это сборка активов вашего проекта, которые вы собрали для тестирования, развертывания или распространения вашего программного решения или его части. Примерами являются набор скомпилированных классов Java или приложения Java, упакованных в архив Java, веб-приложение в виде структуры каталогов или архива веб-приложений и т. д.

Артефакт - это некая выходная сборка вашего проекта. В общем случае их может быть несколько: jar для десктопа и .war для веба ну и т.д.

Для каждого артефакта можно определить правила сборки, развертывания, запуска и т.д.

Есть артефакты в смысле Maven - это все тот же архив, но предназначенный для деплоймента на репозиторий maven
+ [к оглавлению](#spring)


## В чем отличие артефакта war от war exploded?
__Web Archive или Web Application Resource__ — формат файла, описывающий, как полное веб-приложение упаковывается в соответствии со спецификацией Java-сервлетов в файл в формате JAR или ZIP. Такие файлы имеют расширение «.war» и поэтому называются ещё «WAR-файлами».

war создаст только один файл war (который является просто архивом), а вариант с exploded — это просто «распакованный» war. Такой вариант позволяет быстрее деплоить мелкие изменения на сервер.
+ [к оглавлению](#spring)


## Какая разница между аннотациями @Component, @Repository и @Service в Spring?
Все они определяют бины Spring. Однако между ними всё же есть разница.

+ __@Component__ — универсальный компонент
+ __@Repository__ — компонент, который предназначен для хранения, извлечения и поиска. Как правило, используется для работы с базами данных.
+ __@Service__ — фасад для некоторой бизнес логики

Пользовательские аннотации, производные от `@Component`, могут добавлять специальную логику в бинах.

Например, бины, получившиеся при помощи `@Repository`, дополнительно имеют обработку для JDBC Exception.

`@Service` в настоящее время является псевдонимом `@Component`. Однако, в официальной документации Spring рекомендуется использовать именно `@Service` для бизнес логики. Вполне возможно, что в будущих версиях фреймворка, для данного стереотипа добавится дополнительная семантика, и его бины станут обладать дополнительной логикой.
+ [к оглавлению](#spring)


## Как выглядит структура MVC-приложения?
__MVC расшифровывается как Model — View — Controller.__ Это тип архитектуры приложения в которой логические части приложения условно разбиваются на три блока:
+ Модель
+ Вид
+ Контроллер

+ __Модель__  — отвечает за поведение приложения независимо от интерфейса пользователя. Модель относится к полному управлению данными, логикой и правилами приложения.
+ __Вид__ — это внешняя составляющая приложения. Это может быть HTML страница, диаграмма или UI.
+ __Контроллер__ — отвечает за получение входных и поток исходных данных. В его функции входит отслеживание действий пользователя.

Можно рассмотреть эту модель на примере кафе.
Официант — это контроллер. Он знает все варианты блюд из меню и может передать ваш заказ на кухню.
Повара на кухне — это модель. Они знают, какие взять ингредиенты и что с ними сделать, чтобы выполнить конкретный заказ.
Борщ — это представление. Речь об итоговом продукте, который пользователь сначала заказывает, а потом получает.
+ [к оглавлению](#spring)


## Какая основная зависимость фреймворка Спринг? Почему во многих сборках она не указывается явно?
+ __spring-core__ Т.к. включена во все артефакты.
+ [к оглавлению](#spring)


## Чем контроллер отличается от сервлета?
сервлет и контроллер Spring MVC могут использоваться для одного и того же, но они действуют на другом уровне приложения Java

сервлет является частью J2EE framework, и каждый сервер приложений Java (Tomcat, Jetty и т. д.) построен для запуска сервлетов. Сервлет-это слой "низкого уровня" в стеке J2EE. Тебе не нужен сервлет.jar для запуска приложения, потому что он упакован с сервером приложений

контроллер Spring MVC-это библиотека построенный на сервлете, чтобы сделать вещи проще. Spring MVC предлагает более встроенные функции, такие как параметр формы для отображения параметров метода контроллера, упрощение обработки двоичных представлений формы (т. е. когда ваша форма может загружать файлы). Вам нужно упаковать необходимые банки в приложение, чтобы запустить контроллер Spring MVC

вы должны использовать сервлет, когда вам нужно идти "низкий уровень", и пример может быть по причине производительности. Spring MVC работает хорошо, но если он имеет некоторые накладные расходы, если вам нужно выжать все, что вы можете с вашего сервера приложений (и вы уже настроили другие слои, такие как db), идут с сервлетом. Вы можете выбрать сервлет, если хотите понять основы веб-спецификаций J2EE (т. е. для образовательных целей)

во всех остальных случаях вы можете/должны выбрать веб-фреймворка. Spring MVC-один из них; с Spring MVC вам не нужно изобретать колесо (i.e бинарное управление формой, параметр формы к преобразование фасоли,проверка параметров и так далее). Еще один плюс Spring MVC заключается в том, что в одном классе вы можете легко управлять вводом из разных URL-адресов и методов, делая то же самое в сервлете, но код более сложный и менее читаемый. Я считаю, что Spring MVC хорош для создания служб rest и управления простыми приложениями (i.e веб-приложение с простыми формами). Если вам нужно управлять очень сложными формами с Ajax, вложенными формами и приложением с сеансом и состояние страницы мой совет-переключиться на компонентную структуру (например,apache калитка например).
+ [к оглавлению](#spring)


## Как вернуть страницу в контроллере? Как вернуть данные?



+ [к оглавлению](#spring)


## Как интегрировать Hibernate и Spring?
Оба фреймворка поддерживают интеграцию из коробки и в общем настройка их взаимодействия не составляет труда. Общие шаги выглядят следующим образом.

+ 1.Добавить зависимости для hibernate-entitymanager, hibernate-core и spring-orm.
+ 2.Создать классы модели и передать реализации DAO операции над базой данных. Важно, что DAO классы используют SessionFactory, который внедряется в конфигурации бинов Spring.
+ 3.Настроить конфигурационный файл Spring для Hibernate.
+ 4.Дополнительно появляется возможность использовать аннотацию @Transactional и перестать беспокоиться об управлении транзакцией Hibernate.
+ [к оглавлению](#spring)






# Spring Security

## Как подключить Spring Security к проекту?
+ 1.Добавить зависимость в `Maven` __spring-security-config__
+ 2.Добавить классы конфигурации:
+ наследник для __AbstractSecurityWebApplicationInitializer__ - 
__SpringSecurityInitializer__ - обязателен для не boot-приложения. Кода в нем нет, но требуется для регистрации секьюрити в Спринг-контейнере.
+ наследник для __WebSecurityConfigurerAdapter__ с аннотацией `@EnableWebSecurity` - __SecurityConfig__ - настройка секьюрности по определенным URL, а также настройка __UserDetails и GrantedAuthority__.
+ реализация интерфейса __AuthenticationSuccessHandler__ - для стартового перенаправления вновь авторизованного пользователя
+ 3.Добавить реализацию интерфейсов __UserDetails и GrantedAuthority__ в классах-сущностях (например `User` и `Role`) с переопределением существующих методов:
```java
для UserDetails:
	Collection<? extends GrantedAuthority> getAuthorities();
	String getPassword();
	String getUsername();
	boolean isAccountNonExpired();
	boolean isAccountNonLocked();
	boolean isCredentialsNonExpired();
	boolean isEnabled();
для GrantedAuthority:
	String getAuthority() 
```
+ 4.Добавить реализацию интерфейса __UserDetailsService__ с реализацией единственного метода:
`UserDetails loadUserByUsername(String username)`
+ 5.Настроить способ аутентификации в __SecurityConfig__ переопределив метод
	`void configure(AuthenticationManagerBuilder auth)`
+ 6.Настроить доступ к частям сайта в __SecurityConfig__ переопределив метод
	`void configure(HttpSecurity http)`
+ [к оглавлению](#spring)


## Как мы можем добавить секьюрность к контроллеру? (минимум 2 способа).
+ Через конфиг `hasRole`, `hasAuthority`
+ Через аннотации `@PreAuthorize("hasAuthority('ADMIN')")`, `@PostAuthorize`, `@Secured`, `@RoleAllowed`, `@PreFilter` и `@PostFilter` 
+ через Thymeleaf: (получилось только в Spring Boot)
добавить зависимость `thymeleaf-extras-springsecurity5`
далее в html: 
```
	#authentication.principal....(разные методы).
	sec:authorize
	sec:authentication
```
+ [к оглавлению](#spring)


## Что будет являться эквивалентом пользователя и роли в приложении со Spring Security?
`Spring Security` базируется на 2х интерфейсах, которые определяют связь сущностей с секьюрностью: `UserDetails` и `GrantedAuthority`.
+ __UserDetails__ - то, что будет интерпретироваться системой как пользователь.
+ __GrantedAuthority__ - сущность, описывающая права юзера.
+ [к оглавлению](#spring)


## Какие варианты хранения информации о пользователях вы знаете?
Есть несколько стандартных типов хранения и извлечения пользователя, и за каждый из них отвечает свой `AuthenticationProvider`. 
`AuthenticationManager` делегирует провайдеру извлечь данные их хранилища. В `Spring Security` реализованы несколько стандартных провайдеров, все они задаются в методе `configure()`:
```java
@EnableWebSecurity(debug = true)
public class SecurityConfig extends WebSecurityConfigurerAdapter 
   @Override
    public void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication()
                ....
    }
...
}
```
Итак, провайдеры:
+ __In-Memory__ – простейший, задан в вышеприведенном фрагменте кода
+ __Jdbc__ –  хранение в бд
+ __LDAP__
[Подробнее-->](https://sysout.ru/kak-ustroena-autentifikatsiya-v-spring-security/)
+ [к оглавлению](#spring)


## Аутентификация и Авторизация - в чём разница?
Идентификация, аутентификация и авторизация – три процесса защищающие данные от доступа посторонних лиц.
+ __Идентификация__ — процесс распознавания пользователя по его идентификатору.
+ __Аутентификация__ — процедура проверки подлинности, доказательство что пользователь именно тот, за кого себя выдает.
+ __Авторизация__ — предоставление определённых прав.

Механизмы идентификации, аутентификации и авторизации рассмотрим на примере сайта банка.

Находясь на сайте банка, пользователь решает зайти в личный кабинет, чтобы сделать денежный перевод. На странице личного кабинета система вначале просит ввести идентификатор. Это может быть логин, имя и фамилия, адрес электронной почты или номер мобильного телефона.

Какой конкретно вид данных необходимо ввести – зависит от ресурса. 

Данные, которые указывались при регистрации, необходимо ввести для получения доступа. Если при регистрации указывалось несколько типов данных – и логин, и адрес электронной почты, и номер мобильного, то система сама подскажет что ей конкретно нужно.

Ввод этих данных необходим для идентификации человека за монитором как пользователя конкретно этого банка.

Если пользователь в качестве идентификатора ввел «Александр Петров», и система нашла в своей базе запись о пользователе с таким именем, то идентификация завершилась.

После идентификации следует процесс аутентификации, в котором пользователю нужно доказать, что он является человеком, который регистрировался под именем Александр Петров.

Для доказательства необходимо наличие одного из типов аутентификационных данных:
Нечто, присущее только пользователю. Биометрические данные: сканеры лица, отпечатки пальцев или сетчатки глаза.
Нечто, известное только пользователю. Сюда относятся pin-коды, пароли, графические ключи, секретные слова.
Нечто, имеющееся у пользователя. В данном качестве может выступать токен, то есть компактное устройство, предназначенное для обеспечения информационной безопасности пользователя, также используется для идентификации владельца. Самые простые токены не требуют физического подключения к компьютеру – у них имеется дисплей, где отображается число, которое пользователь вводит в систему для осуществления входа; более сложные подключаются к компьютерам посредством USB и Bluetooth-интерфейсов.
Самый распространенный тип аутентификационных данных – это пароль. Именно поэтому так важно создавать и правильно хранить свои пароли. 

После ввода пользователем пароля система проверяет: соответствует ли условный пароль «Q45fp02@13» пользователю с именем Александр Петров. Таким образом происходит аутентификация.

Если все верно, и пара логин-пароль верны, то система предоставит пользователю доступ к его ресурсам и совершение банковских операций, то есть произойдет авторизация.

Описанные процессы всегда происходят только в таком порядке: идентификация, аутентификация, авторизация. Вся цепочка потеряет смысл, если, например, сайт сначала предоставит доступ к денежным средствам пользователя, а потом будет уточнять, он ли это на самом деле.

Процессы идентификации, аутентификации и авторизации характерны не только для онлайн-банкинга, но и для электронной почты, социальных сетей и других ресурсов.

В реальной жизни мы также сталкиваемся идентификацией, аутентификацией и авторизацией. Примером может служить проверка документов сотрудником полиции. Вы представились как Александр Петров, и сотрудник полиции идентифицировал Вас как Александра Петрова. Для аутентификации необходим паспорт, в котором видно, что Александр Петров выглядит так же, как и вы. Авторизацией в данном случае будет то, что сотрудник отпустит вас и пожелает счастливого пути, т.е. предоставит право свободного перемещения.

Процессы идентификации, аутентификации и авторизации есть во многих сферах. 

Даже в простейших детских сказках. Сказка «Волк и семеро козлят» является идеальным примером для демонстрации.

Здесь козлята выступают в роли системы безопасности, идентифицируя каждого, кто подходит к двери. В качестве данных для аутентификации выступает биометрия – тонкий голосок мамы-козы. И если в первый раз волк не смог пройти аутентификацию (его выдал грубый голос), то со второй попытки (после того как ему перековали горло, и он запел тонким голоском) он аутентифицировался как мама-коза и козлята «авторизовали» его в свою избу.

Несмотря на то, что сказка закончилась благополучно, доступ к козлятам был получен неправомерно. Волку удалось обмануть процессы идентификации и аутентификации и тем самым пройти авторизацию.

Если в старой детской сказке это оказалось возможным, то что говорить о современных злоумышленниках. Чтобы защитить свои денежные средства и персональные данные и козлят от волка от злоумышленника необходимо использовать более сложные способы аутентификации.
+ [к оглавлению](#spring)
