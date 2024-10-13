Tags:
- [[Java]]

## Description

In Java, a data type is a classification that specifies the type of data that a variable can hold. It defines the size of memory allocated to the variable and the operations that can be performed on that data


![[Data-Types.webp]]
### Code summary
```java
public class DataTypesExample {
    public static void main(String[] args) {
        // Primitive data types
        byte byteValue;               // 8-bit signed integer
        short shortValue;             // 16-bit signed integer
        int intValue;                 // 32-bit signed integer
        long longValue;               // 64-bit signed integer
        float floatValue;             // 32-bit floating-point
        double doubleValue;           // 64-bit floating-point
        char charValue;               // 16-bit Unicode character
        boolean booleanValue;         // true or false

        // Non-primitive data types
        String stringValue;           // String (sequence of characters)
        Integer integerValue;         // Wrapper class for int
        Double doubleObjValue;        // Wrapper class for double
        int[] intArray;               // Array of integers
        ArrayList<String> stringList; // ArrayList of Strings
        HashMap<String, Integer> map; // HashMap with String keys and Integer values
        Object objectValue;           // Object (base class for all objects)
    }
}

```