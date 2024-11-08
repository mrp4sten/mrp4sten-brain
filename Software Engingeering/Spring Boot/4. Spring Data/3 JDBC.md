Tags: 
- [[Java]]
- [[0 Spring Boot]]

# Spring Data JDBC

Spring Data JDBC is a part of the Spring Data project that provides support for using JDBC (Java Database Connectivity) to interact with relational databases. It is designed to provide a simple and consistent programming model for interacting with databases using JDBC, while still allowing for the full power of JDBC to be used if needed. Spring Data JDBC provides a set of abstraction and utility classes that simplify the task of working with databases, such as a simple template class for executing SQL queries, a repository abstraction for implementing data access objects (DAOs), and support for pagination and sorting of query results. It works with both Java and Kotlin.

**Key Features:**

1. **No ORM Layer:** Spring Data JDBC does not use an ORM like Hibernate. It works directly with JDBC and focuses on simplifying CRUD operations while maintaining a simple, efficient approach.
2. **Repository Abstraction:** Similar to Spring Data JPA, you can define repositories that extend `JdbcRepository` or `CrudRepository`, which provide built-in methods for managing entities.
3. **Less Overhead:** Since it doesn't use an ORM, Spring Data JDBC is lighter and faster for many use cases, making it suitable for simpler or more performance-sensitive applications.