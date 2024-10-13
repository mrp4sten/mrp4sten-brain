Tags: 
- [[Collections]]
- [[Java]]
## Description
This collection implements the Set interface backed by hash table. This class permits the null element. The class also offers constant time performance for the basic operations like add, remove, contains and size assuming the hash function disperses the elements properly among the buckets
### Example 
```java
// Java program to illustrate the concept
// of Collection objects storage in a HashSet
import java.io.*;
import java.util.*;

class CollectionObjectStorage {
  
    public static void main(String[] args)
    {
        // Instantiate an object of HashSet
        HashSet<ArrayList> set = new HashSet<>();

        // create ArrayList list1
        ArrayList<Integer> list1 = new ArrayList<>();

        // create ArrayList list2
        ArrayList<Integer> list2 = new ArrayList<>();

        // Add elements using add method
        list1.add(1);
        list1.add(2);
        list2.add(1);
        list2.add(2);
        set.add(list1);
        set.add(list2);

        // print the set size to understand the
        // internal storage of ArrayList in Set
        System.out.println(set.size());
    }
}
```

![[HowHashSetWorks.webp]]