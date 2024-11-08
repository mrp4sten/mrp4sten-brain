Tags: 
- [[Java]]
- [[0 Spring Boot]]

Spring Security supports a variety of authentication mechanisms, such as username and password authentication, OAuth2, and more. Once a user is authenticated, Spring Security can then be used to authorize that user’s access to specific resources or functionality. There are several annotations that can be used to control access to specific methods or classes.

**Basic example**
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
            .antMatchers("/admin/**").hasRole("ADMIN")   // Only allow ADMIN role to access /admin/** endpoints
            .antMatchers("/user/**").hasAnyRole("USER", "ADMIN") // USER and ADMIN can access /user/**
            .anyRequest().authenticated()  // All other requests must be authenticated
            .and()
            .formLogin(); // Enable form login
    }
}

```
