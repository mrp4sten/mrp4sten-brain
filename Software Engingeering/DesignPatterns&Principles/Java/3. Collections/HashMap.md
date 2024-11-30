Tags: 
- [[Collections]]
- [[Java]]
## Description
This collection provides implementation of [[Map]] interface of Java. But this collection saves Key and Value pairs like a JSON: (key: name, value: Mauricio)
```json
{
 "name": "Mauricio"
}
```

### Example
```java
import java.util.HashMap;

public class HashMapCreation {
    public static void main(String args[]) {
        
        // Create a HashMap of Integer keys and String values
        HashMap<Integer, String> hashMap = new HashMap<>();
        
        // Displaying the HashMap (which is empty at this point)
        System.out.println("HashMap Elements: " + hashMap);
    }
}
```

![[java-hashmap-entry-impl.png]]