Tags: 
- [[Collections]]
- [[Java]]
## Description
TreeSet is one of the most important implementations of the SortedSet interface in Java that uses a Tree for storage. The ordering of the elements is maintained by a set using their natural ordering whether or not an explicit comparator is provided. This must be consistent with equals if it is to correctly implement the Set interface. 
![[treeset.jpg]]
## Example
```java
import java.util.TreeSet;

public class TreeSetCreation {
    public static void main(String args[]) {
        // Create a TreeSet of Strings
        TreeSet<String> treeSet = new TreeSet<>();
        
        // Displaying the TreeSet (which is empty at this point)
        System.out.println("TreeSet elements: " + treeSet);
    }
}

```
