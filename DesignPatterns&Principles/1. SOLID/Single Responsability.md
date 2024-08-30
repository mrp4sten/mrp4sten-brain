Tags:
- [[SOLID]]
- [[Design Patterns]]
- [[Design Principles]]
- [[Programming]]

## Description
This principle states that a class should only have one responsibility. Furthermore, it should only have one reason to change.

## Pros
1. **Testing** : A class with one responsability will have far fewer test cases
2. **Lower coupling** : Less functionality in a single class will have fewer dependencies
3. **Organization** : Smaller well-organized classes are easier to search than monolithic ones.

```java
// Sample without Single Responsability
public class User {
    private String name;
    private String email;
    
    public User(String name, String email) {
        this.name = name;
        this.email = email;
    }
    
    // Getter and Setter methods
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getEmail() {
        return email;
    }
    
    public void setEmail(String email) {
        this.email = email;
    }
    
    // Method for user report generation
    public String generateReport() {
        return "User Report: Name = " + name + ", Email = " + email;
    }
}
 
```

```java
// Sample with Single Responsability
// Class responsible for user data management
public class User {
    private String name;
    private String email;
    
    public User(String name, String email) {
        this.name = name;
        this.email = email;
    }
    
    // Getter and Setter methods
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getEmail() {
        return email;
    }
    
    public void setEmail(String email) {
        this.email = email;
    }
}

// Class responsible for generating user reports
public class UserReportGenerator {
    public String generateReport(User user) {
        return "User Report: Name = " + user.getName() + ", Email = " + user.getEmail();
    }
}

```