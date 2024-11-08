Tags: 
- [[Java]]
- [[0 Spring Boot]]

# Mock MVC

Spring’s MockMvc is a class that allows you to test Spring MVC controllers without the need for an actual web server. It is part of the Spring Test module, which provides a set of testing utilities for Spring applications.

```java
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.result.MockMvcResultMatchers;

@WebMvcTest(MyController.class)  // Test only MyController
public class MyControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    public void testSayHello() throws Exception {
        // Perform a GET request to /hello and expect status 200 OK and content "Hello, World!"
        mockMvc.perform(get("/hello"))
                .andExpect(status().isOk())  // Check for 200 OK status
                .andExpect(content().string("Hello, World!"));  // Check the response content
    }
}

```