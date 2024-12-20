Tags: 
- [[Java]]
- - [[Software Engineering]]

Spring Boot is a framework for building applications based on the Spring Framework, a widely-used, open-source framework for building Java-based enterprise applications. Spring Boot aims to make it easy to create stand-alone, production-grade Spring-based applications that you can “just run”.
# Terminology

Spring Core is the foundation of the Spring Framework, which provides a comprehensive programming and configuration model for Java-based applications. Here are some key terms and concepts related to Spring Core:

- **Beans**: In Spring, a “bean” is a Java object that is managed by the Spring container. Beans are typically defined using configuration metadata, which can be specified in XML, Java annotations, or Java code.
- Inversion of Control (**IoC**): One of the main principles of Spring is Inversion of Control (IoC), which means that the Spring container is responsible for managing the lifecycle of beans and injecting their dependencies.
- Dependency Injection (**DI**): Spring uses Dependency Injection (DI) to manage the dependencies between beans. In DI, an object’s dependencies are provided to it by the container, rather than the object creating or looking up its own dependencies.
- **Container**: The Spring container is the core part of the Spring Framework, which creates and manages beans and their dependencies.
- **ApplicationContext**: An ApplicationContext is an implementation of the Spring container. It is responsible for loading and managing the configuration metadata and creating the beans defined in that metadata.
- Aspect-Oriented Programming (**AOP**): Spring supports Aspect-Oriented Programming (AOP), which allows you to separate cross-cutting concerns, such as logging or security, from the business logic of your application.
- **Events**: Spring provides an event model that allows beans to send and receive events. This is used to decouple the beans from each other, making the application more loosely coupled.
- **ApplicationEvent** and **listener**: Spring support publish subscribe model for event handling, ApplicationEvent defines event object, and the listener is a class that implements ApplicationListener interface, listening for the specific event and take the necessary action.
- **Data Access**: Spring provides a consistent, high-level abstraction for data access using various frameworks like JDBC, Hibernate, JPA.
- **Transactions**: Spring provides a flexible, consistent and easy way to declaratively manage transactions with different underlying technologies such as JPA, JDBC, and Hibernate.
- **Task Execution and Scheduling**: Spring provides a TaskExecutor and TaskScheduler, providing a convenient way to run tasks concurrently, on a scheduled basis or asynchronously.
# Architecture

Spring Boot follows a layered architecture in which each layer communicates with the layer directly below or above (hierarchical structure) it. There are four layers in Spring Boot are as follows:

- **Presentation Layer**: handles the HTTP requests, translates the JSON parameter to object, and authenticates the request and transfer it to the business layer.
- **Business Layer**: The business layer handles all the business logic. It consists of service classes and uses services provided by data access layers. It also performs authorization and validation.
- **Persistence Layer**: The persistence layer contains all the storage logic and translates business objects from and to database rows.
- **Database Layer**: In the database layer, CRUD (create, retrieve, update, delete) operations are performed.