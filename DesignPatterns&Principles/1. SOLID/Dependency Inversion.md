Tags:
- [[SOLID]]
- [[Design Patterns]]
- [[Design Principles]]
- [[Programming]]
## Description
Basically this principle reduce dependencies between modules(low and high)

> 1. High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g., interfaces).
> 2. Abstractions should not depend on details. Details should depend on abstractions.

### Samples without Dependency inversion
```java
// Low-level module
public class UserRepository {
    public void saveUser(String user) {
        // Save user to a database
        System.out.println("User saved to database: " + user);
    }
}

// High-level module
public class UserService {
    private UserRepository userRepository;
    
    public UserService() {
        this.userRepository = new UserRepository(); // Direct dependency
    }
    
    public void registerUser(String user) {
        // Some business logic
        userRepository.saveUser(user);
    }
}

```

### Sample with Dependency Inversion
```java
// Abstraction
public interface UserRepository {
    void saveUser(String user);
}

// Low-level module
public class DatabaseUserRepository implements UserRepository {
    @Override
    public void saveUser(String user) {
        // Save user to a database
        System.out.println("User saved to database: " + user);
    }
}

// Another low-level module (e.g., saving to a file)
public class FileUserRepository implements UserRepository {
    @Override
    public void saveUser(String user) {
        // Save user to a file
        System.out.println("User saved to file: " + user);
    }
}

// High-level module
public class UserService {
    private UserRepository userRepository;
    
    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository; // Dependency injection
    }
    
    public void registerUser(String user) {
        // Some business logic
        userRepository.saveUser(user);
    }
}

public class Main {
    public static void main(String[] args) {
        // Using database repository
        UserRepository databaseRepo = new DatabaseUserRepository();
        UserService userServiceWithDatabase = new UserService(databaseRepo);
        userServiceWithDatabase.registerUser("Alice");
        
        // Using file repository
        UserRepository fileRepo = new FileUserRepository();
        UserService userServiceWithFile = new UserService(fileRepo);
        userServiceWithFile.registerUser("Bob");
    }
}


```