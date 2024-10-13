Tags: 
- [[Collections]]
- [[Java]]
## Description
Is part of  the java collections framework and it is a class of java.util package. It provides us with dynamic arrays in Java.

### Example (from https://www.geeksforgeeks.org/arraylist-in-java/#java-arraylist-example)
```java
// Java program to demonstrate the
// working of ArrayList
import java.io.*;
import java.util.*;

class ArrayListExample {
    public static void main(String[] args)
    {
        // Size of the
        // ArrayList
        int n = 5;

        // Declaring the ArrayList with
        // initial size n
        ArrayList<Integer> arr1 = new ArrayList<Integer>(n);

        // Declaring the ArrayList
        ArrayList<Integer> arr2 = new ArrayList<Integer>();

        // Printing the ArrayList
        System.out.println("Array 1:" + arr1);
        System.out.println("Array 2:" + arr2);

        // Appending new elements at
        // the end of the list
        for (int i = 1; i <= n; i++) {
            arr1.add(i);
            arr2.add(i);
        }

        // Printing the ArrayList
        System.out.println("Array 1:" + arr1);
        System.out.println("Array 2:" + arr2);
    }
}

/**
Output: 

	Array 1:[]
	Array 2:[]
	Array 1:[1, 2, 3, 4, 5]
	Array 2:[1, 2, 3, 4, 5]
**/
```

![[ArrayList_Integer_Object.png]]
