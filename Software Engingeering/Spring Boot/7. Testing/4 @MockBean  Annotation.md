Tags: 
- [[Java]]
- [[0 Spring Boot]]

# @MockBean Annotation

`MockBean` is a Spring annotation that can be used to create a mock implementation of a bean in the Spring application context. When a test is annotated with MockBean, Spring creates a mock implementation of the specified bean and adds it to the application context. The mock bean can then be used to replace the real bean during testing.

```java
import org.junit.jupiter.api.Test;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.boot.test.mock.mockito.MockBean;
import org.springframework.http.MediaType;
import org.springframework.test.web.servlet.MockMvc;

import java.util.Arrays;
import java.util.List;

import static org.mockito.Mockito.when;
import static org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.status;
import static org.springframework.test.web.servlet.result.MockMvcResultMatchers.content;

@WebMvcTest(PersonController.class)  // Test only the controller layer
public class PersonControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean  // This will mock the PersonRepository bean in the application context
    private PersonRepository personRepository;

    @Test
    public void testGetAllPersons() throws Exception {
        // Given: Mock data returned by the repository
        Person person1 = new Person("John", "Doe");
        Person person2 = new Person("Jane", "Smith");

        List<Person> persons = Arrays.asList(person1, person2);

        // Mock the behavior of the repository
        when(personRepository.findAll()).thenReturn(persons);

        // When: Send GET request to /persons
        mockMvc.perform(get("/persons"))
                .andExpect(status().isOk())  // Expect HTTP 200 OK
                .andExpect(content().json("["
                        + "{\"firstName\": \"John\", \"lastName\": \"Doe\"},"
                        + "{\"firstName\": \"Jane\", \"lastName\": \"Smith\"}"
                        + "]"));
    }
}

```