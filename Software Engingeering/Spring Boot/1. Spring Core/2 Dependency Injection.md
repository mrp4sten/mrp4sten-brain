Tags: 
- [[Java]]
- [[0 Spring Boot]]
- [[3 IOC]]

Spring Boot uses the Spring Framework’s Inversion of Control (IoC) container to manage objects and their dependencies. The IoC container is responsible for creating objects, wiring them together, and managing their lifecycle. When an object is created, its dependencies are also created and injected into the object.

### **Types of Dependency Injection**

Spring Boot supports different types of Dependency Injection:

- **Constructor Injection**: Dependencies are passed to the class through its constructor. This is the recommended approach because it ensures that the object is created with all necessary dependencies and supports immutability.
- **Setter Injection**: Dependencies are provided through setter methods. This is useful for optional dependencies but can lead to mutable objects.
- **Field Injection**: Dependencies are injected directly into fields using the `@Autowired` annotation. While convenient, it is generally discouraged in favor of constructor injection, as it can make testing and understanding dependencies harder.