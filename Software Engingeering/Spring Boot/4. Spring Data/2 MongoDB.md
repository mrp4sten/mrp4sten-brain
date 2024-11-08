Tags: 
- [[Java]]
- [[0 Spring Boot]]

# Spring Data Mongodb

Spring Data for MongoDB is part of the umbrella Spring Data project which aims to provide a familiar and consistent Spring-based programming model for new datastores while retaining store-specific features and capabilities

The Spring Data MongoDB project provides integration with the MongoDB document database. Key functional areas of Spring Data MongoDB are a POJO centric model for interacting with a MongoDB DBCollection and easily writing a Repository style data access layer.

**Key Features:**

1. **Repository Abstraction:** Similar to JPA, Spring Data MongoDB allows you to create repository interfaces for your documents that extend `MongoRepository` or `CrudRepository`, which provides many built-in methods like `save()`, `findById()`, and `delete()`.
2. **Custom Queries:** Supports creating custom queries with method names, or using the `@Query` annotation to define more complex queries.
3. **MongoTemplate:** Provides a low-level alternative to `MongoRepository` for more customized queries and operations.