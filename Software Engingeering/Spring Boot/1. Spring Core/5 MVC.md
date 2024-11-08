Tags:
- [[Java]]
- [[0 Spring Boot]]

Spring MVC is a framework for building web applications in Java. It is part of the Spring Framework, which is a larger ecosystem of tools for building Java applications. Spring MVC is built on the Model-View-Controller (MVC) design pattern, which helps to separate the concerns of the application into three distinct components: the Model, the View, and the Controller.
![[spring-web-model-view-controller.png]]
- **Model** - A model contains the data of the application. A data can be a single object or a collection of objects.
- **Controller** - A controller contains the business logic of an application. Here, the @Controller annotation is used to mark the class as the controller.
- **View** - A view represents the provided information in a particular format. Generally, JSP+JSTL is used to create a view page. Although spring also supports other view technologies such as Apache Velocity, Thymeleaf and FreeMarker.
- **Front Controller** - In Spring Web MVC, the DispatcherServlet class works as the front controller. It is responsible to manage the flow of the Spring MVC application.