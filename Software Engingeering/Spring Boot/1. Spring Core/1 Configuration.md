Tags: 
- [[Java]]
- [[0 Spring Boot]]}
### 1. **Application Properties and YAML**

- **Properties File**: `application.properties` or `application.yml` is where configuration settings are typically defined. You can set various application properties here, such as database settings, server ports, and logging levels.
- **YAML**: YAML files (`application.yml`) are a popular alternative to `.properties` files due to their readability and hierarchical structure. This format is especially useful for nested configuration properties.

### 2. **Externalized Configuration**

- Spring Boot supports **externalized configuration**—meaning you can override application settings from different sources like environment variables, command-line arguments, system properties, and external property files.
- This allows for flexible configuration management across different environments (e.g., development, testing, production).

### 3. **Profiles**

- **Profiles** are a powerful way to handle different configurations for different environments. You can define properties specific to each profile (e.g., `application-dev.properties` for development or `application-prod.properties` for production).
- When you activate a specific profile (e.g., `dev` or `prod`), Spring Boot will load the properties specific to that profile.

### 4. **Auto-Configuration**

- Spring Boot’s **auto-configuration** feature automatically configures components based on the dependencies available on the classpath.
- For example, if you include a database dependency like H2 or MySQL, Spring Boot will automatically configure a `DataSource` bean for database access without requiring explicit configuration.

### 5. **Configuration Properties Binding**

- Spring Boot offers **type-safe configuration** by binding properties to Java objects using the `@ConfigurationProperties` annotation.
- This allows developers to group related settings into dedicated classes, making the configuration more organized and easier to manage.

### 6. **Custom Configuration Beans**

- You can create custom configuration beans using the `@Bean` annotation within a `@Configuration` class to define your own configuration logic for specific components.
- This allows you to go beyond auto-configuration when you need finer control over specific beans or components.

### 7. **Environment-Specific Properties and Secrets**

- Spring Boot allows **secure configuration of sensitive data**, such as API keys and passwords, using environment variables or external secret management solutions.
- By avoiding hardcoded secrets in the codebase, this approach improves security.

### 8. **Spring Boot DevTools**

- **DevTools** is a development-time feature that provides live-reload and automatic configuration reload upon code changes, making testing and debugging configurations faster and more efficient.

### 9. **Logging Configuration**

- Spring Boot provides default logging configurations, but you can easily customize the logging behavior by modifying the `application.properties` or adding a `logback.xml` configuration file.
- Log levels can be adjusted per package, and the logging format can be customized to suit the application’s needs.

### 10. **Overriding Defaults**

- You can override default configurations by setting your own properties or beans. Spring Boot makes it easy to replace default behaviors with custom implementations when needed.