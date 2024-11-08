Tags: 
- [[Java]]
- [[0 Spring Boot]]

Spring Data is a collection of projects for data access in Spring-based applications. It provides a common interface for working with various types of data stores, including relational databases, NoSQL data stores, and cloud-based data services.

![[spring_data_overview_small.webp]]

# Spring Data JPA

Spring Data JPA is a library that makes it easy to implement Java Persistence API (JPA) based repositories (a fancy word for “DAO”) for Spring applications. It’s an abstraction on top of JPA that allows you to use a simpler and more convenient API for performing CRUD (Create, Read, Update, Delete) operations on databases. Spring Data JPA also provides additional functionality such as pagination, dynamic query generation, and more.

**Key Features:**

1. **Repository Interfaces:** Spring Data JPA simplifies the creation of data access layers by using repository interfaces that extend `JpaRepository` or `CrudRepository`. These interfaces come with built-in methods like `save()`, `findById()`, `delete()`, and more.
2. **Custom Queries:** You can define custom queries using the `@Query` annotation or by deriving queries directly from the method names.
3. **Pagination and Sorting:** It supports easy pagination and sorting, eliminating the need for manual pagination handling.