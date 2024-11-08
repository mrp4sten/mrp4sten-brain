Tags: 
- [[Java]]
- [[0 Spring Boot]]
# @SpringBootTest annotation

`@SpringBootTest` This annotation is used to create a fully-configured instance of the Spring ApplicationContext for testing. It can be used to test the application’s components, including controllers, services, and repositories, in a real application environment.

```java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.http.MediaType;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.result.MockMvcResultMatchers;
import org.springframework.test.web.servlet.request.MockMvcRequestBuilders;

import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;

@SpringBootTest  // Loads the full Spring context
public class PersonControllerIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Autowired
    private PersonRepository personRepository;

    @BeforeEach
    public void setUp() {
        // Clean up database before each test
        personRepository.deleteAll();
    }

    @Test
    public void testCreatePerson() throws Exception {
        // Given: JSON payload to create a new person
        String personJson = "{\"firstName\": \"John\", \"lastName\": \"Doe\"}";

        // When: Send POST request to /persons
        mockMvc.perform(post("/persons")
                .contentType(MediaType.APPLICATION_JSON)
                .content(personJson))
                .andExpect(status().isCreated())  // Expect HTTP 201 Created status
                .andExpect(content().json("{\"firstName\": \"John\", \"lastName\": \"Doe\"}"));  // Expect the correct response
    }

    @Test
    public void testGetAllPersons() throws Exception {
        // Given: Add some test data
        personRepository.save(new Person("Jane", "Doe"));
        personRepository.save(new Person("John", "Smith"));

        // When: Send GET request to /persons
        mockMvc.perform(MockMvcRequestBuilders.get("/persons"))
                .andExpect(status().isOk())  // Expect HTTP 200 OK status
                .andExpect(MockMvcResultMatchers.jsonPath("$[0].firstName").value("Jane"))
                .andExpect(MockMvcResultMatchers.jsonPath("$[1].firstName").value("John"));
    }
}

```