Tags:
- [[SOLID]]
- [[Design Patterns]]
- [[Design Principles]]
- [[Programming]]
## Description
Larger interfaces should be split into smaller ones. By doing so we can ensure that implementing classes only need to be concerned about the method that are of interest to them.
### Example
```java
// This is a big piece of shit
public interface BearKeeper {
    void washTheBear();
    void feedTheBear();
    void petTheBear();
}

// This is the GOAT!!
public interface BearCleaner { void washTheBear(); } 
public interface BearFeeder { void feedTheBear(); } 
public interface BearPetter { void petTheBear(); }

// And after we are free to implement only the methods that matter to us
public class BearCarer implements BearCleaner, BearFeeder {

    public void washTheBear() {
        //I think we missed a spot...
    }

    public void feedTheBear() {
        //Tuna Tuesdays...
    }
}

```