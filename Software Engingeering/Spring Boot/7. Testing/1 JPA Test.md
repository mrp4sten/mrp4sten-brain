Tags: 
- [[Java]]
- [[0 Spring Boot]]
# JPA Test

Spring JPA (Java Persistence API) is a library that makes it easy to work with databases and other data stores in a Spring application. Spring JPA uses the Java Persistence API (JPA) to interact with databases and provides an abstraction layer to work with different data stores.

Testing in Spring JPA involves testing the application’s persistence layer, which includes the entities, repositories and data access objects (DAOs) that interact with the database. Testing these components separately from the rest of the application helps ensure that the persistence layer is working correctly and that any issues can be identified and addressed without affecting the rest of the application.

There are several ways to test the persistence layer using Spring JPA. One way is to use in-memory databases, such as H2 or Derby, which can be used during testing to mimic the production database. This allows the tests to run quickly and eliminates the need to set up a separate test database. Another way is to use real databases and to use TestContainers to spin up a real instance of the database for testing purpose.

Spring Test module provides different annotations such as @DataJpaTest and @AutoConfigureTestDatabase that facilitates the testing of JPA specific functionality.

Additionally, Spring provides the JPA Testing Utilities, which provides a set of utility classes and annotations to test JPA-based persistence layer easily, such as `@DataJpaTest`, `@AutoConfigureTestDatabase`, and TestEntityManager classes. These utilities can be used to create, read, update, and delete entities, perform JPA queries, and interact with the database during the test.

Testing the persistence layer separately from the rest of the application allows to catch any issues early in the development process, making it easy to identify and fix bugs and improve the quality of the application.

**Example**

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.orm.jpa.DataJpaTest;
import org.springframework.boot.test.context.SpringBootTest;

import static org.assertj.core.api.Assertions.assertThat;

@DataJpaTest
public class PersonRepositoryTest {

    @Autowired
    private PersonRepository personRepository;

    @BeforeEach
    public void setUp() {
        // This is a setup method, you can use it to initialize data for each test.
        personRepository.deleteAll(); // Ensure the database is clean before each test
    }

    @Test
    public void testSavePerson() {
        // Given
        Person person = new Person("John", "Doe");

        // When
        Person savedPerson = personRepository.save(person);

        // Then
        assertThat(savedPerson).isNotNull();
        assertThat(savedPerson.getId()).isGreaterThan(0);
        assertThat(savedPerson.getFirstName()).isEqualTo("John");
        assertThat(savedPerson.getLastName()).isEqualTo("Doe");
    }

    @Test
    public void testFindByFirstName() {
        // Given
        Person person = new Person("Jane", "Doe");
        personRepository.save(person);

        // When
        Person foundPerson = personRepository.findByFirstName("Jane");

        // Then
        assertThat(foundPerson).isNotNull();
        assertThat(foundPerson.getFirstName()).isEqualTo("Jane");
        assertThat(foundPerson.getLastName()).isEqualTo("Doe");
    }

    @Test
    public void testDeletePerson() {
        // Given
        Person person = new Person("Alice", "Smith");
        personRepository.save(person);

        // When
        personRepository.deleteById(person.getId());

        // Then
        assertThat(personRepository.findById(person.getId())).isEmpty();
    }
}

```