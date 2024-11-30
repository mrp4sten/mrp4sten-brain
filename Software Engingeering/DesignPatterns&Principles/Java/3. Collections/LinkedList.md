Tags: 
- [[Collections]]
- [[Java]]
## Description
This class is an implementation of the LinkedList data structure which is a linear data structure where the elements are not stored in contiguous locations and every element is a separate object with a data part and address part.

Visit this site to see how it works with animations: https://antoniosarosi.github.io/Linked-List-Visualization/
### Example
```java
// Java program to add elements to a LinkedList
import java.util.LinkedList;

public class AddElements {

    // Main driver method
    public static void main(String[] args) {
        // Creating a LinkedList
        LinkedList<String> list = new LinkedList<String>();

        // Adding elements to the LinkedList using add() method
        list.add("One");
        list.add("Two");
        list.add("Three");
        list.add("Four");
        list.add("Five");

        // Printing the LinkedList
        System.out.println(list);
    }
}

```