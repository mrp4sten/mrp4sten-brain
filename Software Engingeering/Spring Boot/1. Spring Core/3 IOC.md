Tags:
- [[Java]]
- [[2 Dependency Injection]]
- [[0 Spring Boot]]

Inversion of Control (IoC) is a design pattern that is often used in conjunction with the Dependency Injection (DI) pattern. The basic idea behind IoC is to invert the flow of control in a program, so that instead of the program controlling the flow of logic and the creation of objects, the objects themselves control the flow of logic and the creation of other objects.

Spring is a popular Java framework that uses IoC and DI to provide a more flexible, modular approach to software development. The Spring IoC container is responsible for managing the creation and configuration of objects in a Spring-based application.

The Spring IoC container creates objects, wires them together, configures them, and manages their complete lifecycle from creation till destruction. This removes the burden of instantiating and configuring objects from the application code, and allows the application code to focus on the business logic rather than on infrastructure concerns.

Spring IoC container provides two ways to configure the objects:

- XML based configuration
- Annotation based configuration

In XML based configuration, you use XML file to describe the configuration metadata and the container creates the objects and wire them together.

In Annotation based configuration, you use annotations in the Java source code to describe the configuration metadata and the container creates the objects and wire them together.

Both way, Spring IoC container can be used to create, manage, and wire together objects in a Spring-based application, using a variety of different strategies, including constructor injection, setter injection, and interface injection.

Overall, Spring IoC container provides a central location to manage the lifecycle and configuration of objects in an application, making it easier to develop, test, and maintain the code.

### **Spring IoC Container**

- The **IoC container** in Spring is a powerful mechanism that manages the lifecycle and configuration of application objects, known as **beans**.
- The container takes care of creating and configuring beans, injecting dependencies, managing the lifecycle, and handling destruction of beans.
- Spring provides two main IoC containers:
    - **BeanFactory**: The basic IoC container that provides foundational dependency injection.
    - **ApplicationContext**: A more advanced container that provides additional features, including event propagation, declarative mechanisms, and AOP integration. This is typically used in Spring Boot applications.
### **How the IoC Container Works**

- **Component Scanning**: When a Spring Boot application starts, the IoC container scans for classes annotated with `@Component`, `@Service`, `@Repository`, and `@Controller` within the specified package and sub-packages.
- **Bean Registration**: These annotated classes are registered as beans in the container.
- **Dependency Injection**: For each bean, the container resolves and injects any dependencies (other beans) that it requires, based on annotations like `@Autowired`.
### **Bean Definition and Configuration**

- Beans can be defined through:
    - **Annotations** (`@Component`, `@Service`, `@Repository`, etc.).
    - **Java-based configuration** with `@Configuration` and `@Bean` annotations.
    - **XML configuration** (though rarely used in modern Spring Boot applications).
- The IoC container then manages these beans throughout their lifecycle.
### **IoC through Dependency Injection**

- **Dependency Injection (DI)** is the implementation mechanism of IoC in Spring. The container “injects” the dependencies a bean needs, either via constructor, setter, or field injection.
- The IoC container handles which beans to inject by looking for `@Autowired` and `@Qualifier` annotations (among others) in the component classes.
- This allows the application components to depend on abstractions rather than specific implementations, making code modular and easier to test.

**Example of IoC**
```java
// UserRepository interface
public interface UserRepository {
    User findUserById(Long id);
}

// UserRepository implementation
@Repository
public class UserRepositoryImpl implements UserRepository {
    @Override
    public User findUserById(Long id) {
        // code to retrieve user
    }
}

// UserService class depends on UserRepository
@Service
public class UserService {
    private final UserRepository userRepository;

    @Autowired
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public User getUser(Long id) {
        return userRepository.findUserById(id);
    }
}
```

- The `UserService` class depends on an implementation of `UserRepository` but doesn’t instantiate it directly. Instead, it relies on the Spring IoC container to provide an instance of `UserRepositoryImpl`.
- The `@Autowired` annotation tells Spring to inject a `UserRepository` bean into the `UserService` constructor.
- Spring automatically scans for and registers `UserRepositoryImpl` as a bean (since it’s annotated with `@Repository`) and injects it where needed.

### **Configuring the IoC Container in Spring Boot**

- In Spring Boot, IoC configuration is simplified. By default, Spring Boot performs **component scanning** on the main application package (the package where the `@SpringBootApplication` annotation resides).
- Spring Boot automatically configures and wires dependencies using sensible defaults, so minimal configuration is required from the developer.
### **Spring Boot’s Auto-Configuration and IoC**

- Spring Boot's **auto-configuration** feature provides pre-configured beans for many common dependencies, like database connections, web servers, and security, further reducing the need for manual configuration.
- For example, if you add `spring-boot-starter-data-jpa` to your project, Spring Boot auto-configures an `EntityManager` and a `DataSource` without any additional setup.