[Java Tutorials](README.md)

# Frameworks
## Various frameworks and plugins

+ [Plugin Lombok](#plugin-lombok)
+ [Framework Apache Maven](#Framwork-Apache-Maven)
+ [Apache Application Server Tomcat](#Apache-Application-Server-Tomcat)
+ [Thymeleaf Templates](#Thymeleaf-Templates)
+ [Framework Swagger](#Framework-Swagger)
+ [Framework Vaadin](#Framework-Vaadin)


+ [ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ](#ССЫЛКИ-НА-ДОПОЛНИТЕЛЬНУЮ-ИНФУ)

## Fram Lombok


+ [Шпаргалки Java программиста 10: Lombok-->]( https://habr.com/ru/post/345520/ )

[к оглавлению](#frameworks)


## Framework Apache Maven

### Использование Dependency
```java
<!-- зависимости от библиотек -->
  <dependencies>
     <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.11</version>
         <scope>test</scope>
    </dependency>
  </dependencies> 
  ```
+ `<dependencies>` – тут мы размещаем список dependency (библиотек), которые используются в проекте;
+ `<dependency>` – библиотека используемая проектом;
+ `<groupId>` – идентификатор группы библиотеки;
+ `<artifactId>` – артефакт (библиотека);
+ `<version>` – версия библиотеки;
+ `<scope>` – этап использования.

### Структура проекта
Корневой каталог проекта:
– pom.xml и все дальнейшие подкаталоги;
– src: все исходные файлы;
+ `src/main:` исходные файлы собственно для продукта;
+ `src/main/java:` Java-исходный текст;
+ `src/main/resources:` другие файлы, которые используются при компиляции или исполнении, например Properties-файлы;
+ `src/test:` исходные файлы, необходимые для организации автоматического тестирования;
+ `src/test/java:` JUnit-тест-задания для автоматического тестирования;
+ `target:` все создаваемые в процессе работы Мавена файлы;
+ `target/classes:` компилированные Java-классы.

### Жизненный цикл
Жизненный цикл проекта — это список поименованных фаз, определяющий порядок действий при его построении.
Maven использует по умолчанию следующий жизненный цикл:
+ 1)__archetype__ – создание темплейта и обработка ресурсов. На этой фазе разрешаются и, при необходимости, скачиваются из интернета зависимости;
+ 2)__compile__ – компиляция;
+ 3)__обработка тестовых ресурсов__ (например — скачивается из интернета JUnit-пакет);
+ 4)__компиляция тестов__ (тестирующие классы не передаются конечным пользователям);
+ 5)__test__ – тестирование;
+ 6)__package__ – упаковка (обычно речь идёт о создании JAR– или WAR-файла);
+ 7)__install__ – инсталляция проекта в локальном Maven-репозитории (теперь он доступен как модуль для других локальных проектов);
+ 8)__deploy__ – инсталляция в удаленном Maven-репозитории (теперь стабильная версия проекта доступна широкому кругу разработчиков).

Maven имеет также стандартный жизненный цикл для чистки (`cleaning`) и для генерации его страницы (`site`). Если бы `clean` было частью обычного жизненного цикла, проект подвергался бы чистке при каждом построении, что нежелательно.

Стандартные жизненные циклы могут быть существенно дополнены Maven-плагинами и Maven-архетипами.

Maven-плагины позволяют вставлять в стандартный цикл новые шаги (например, распределение на сервер приложений) или расширять существующие шаги. Maven-архетипы представляют собой заготовки для различнейших программных пакетов (если они отвечают стандартам Maven-структуры).

+ [Официальный сайт установка-->]( http://maven.apache.org/download.cgi )
+ [Apache Maven Project-->]( https://www.apache-maven.ru/ )
+ [Maven. Часть 1 – Знакомство и настройка-->]( https://devcolibri.com/maven-%D1%87%D0%B0%D1%81%D1%82%D1%8C-1-%D0%B7%D0%BD%D0%B0%D0%BA%D0%BE%D0%BC%D1%81%D1%82%D0%B2%D0%BE-%D0%B8-%D0%BD%D0%B0%D1%81%D1%82%D1%80%D0%BE%D0%B9%D0%BA%D0%B0/ )
+ [Maven. Часть 2 – Dependency-->]( https://devcolibri.com/maven-%d1%87%d0%b0%d1%81%d1%82%d1%8c-2-dependency/ )
+ [Доступно о Maven(2016)-->]( https://www.youtube.com/watch?v=nIzJeTQQXtg&feature=youtu.be )

[к оглавлению](#frameworks)

## Apache Application Server Tomcat
+ [Установка и настройка Tomcat Server-->]( https://o7planning.org/ru/11583/installing-and-configuring-tomcat-server )
+ [Установка SSL(HTTPS) для Tomcat Server-->]( https://o7planning.org/ru/12239/installing-ssl-for-tomcat-server )
+ [Название-->]( Ссылка )

[к оглавлению](#frameworks)

## Thymeleaf Templates

+ [Учебник Thymeleaf: Глава 1. Знакомство-->]( https://habr.com/ru/post/350864/ )
+ [Учебник Thymeleaf: Глава 2. Хорошая виртуальная бакалейная лавка Thymes-->]( https://habr.com/ru/post/350866/ )
+ [Учебник Thymeleaf: Глава 3. Использование Text-->]( https://habr.com/ru/post/350868/ )
+ [Руководство Spring Boot и Thymeleaf-->]( https://o7planning.org/ru/11545/spring-boot-and-thymeleaf-tutorial )
+ [Pуководства Thymeleaf-->]( https://o7planning.org/ru/12345/thymeleaf )
+ [YouTube/ITVDN/Движок HTML шаблонов Thymeleaf. Введение в Thymeleaf. Урок 1-->]( https://www.youtube.com/watch?v=NrTbzfeJcwc )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
[к оглавлению](#frameworks)


## Framework Swagger
### ---Info---
+ [Начало работы с Swashbuckle и ASP.NET Core-->]( https://docs.microsoft.com/ru-ru/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio )
+ [GitHub/Swagger-->]( https://github.com/swagger-api )
+ [API Development for Everyone-->]( https://swagger.io/ )
+ [Swagger Petstore-->]( https://editor.swagger.io/ )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
### ---Video---
+ [ФОРМАЛЬНОЕ ОПИСАНИЕ REST API С ПОМОЩЬЮ SWAGGER (Прохоров Антон)-->]( https://www.youtube.com/watch?v=JeaF0qnWqQY )
+ [014. API + Swagger - Игорь Гусев(2019)-->]( https://www.youtube.com/watch?v=lYjm2w8-ERI )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
### ---Lessons---
+ [Swagger – умная документация вашего RESTful web-API — обзор Junior back-end developer-а для новичков(2018)-->]( https://habr.com/ru/post/434798/ )
+ [Swagger-->]( https://prosto-tak.ru/swagger/ )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
### ---Forum---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
[к оглавлению](#frameworks)



## Framework Vaadin
### ---Info---
+ [Official site vaadin.com-->]( https://vaadin.com/ )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Video---
+ [YouTube/GeekBrains/Основы Vaadin [GeekBrains](2016)-->]( https://www.youtube.com/watch?v=YqApGULVd7s )
+ [YouTube/JUG .ru/Юрий Артамонов — Анатомия и физиология Vaadin Flow(2019)-->]( https://www.youtube.com/watch?v=I-T4dESU-MY )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Lessons---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Forum---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )




## ССЫЛКИ НА ДОПОЛНИТЕЛЬНУЮ ИНФУ
### ---Info---

+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Video---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Lessons---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )

### ---Forum---
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )
+ [Название-->]( Ссылка )




[к оглавлению](#frameworks)
