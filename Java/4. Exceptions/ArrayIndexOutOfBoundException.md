Tags:
- [[Java]]
- [[Exceptions]]
- [[Common Exceptions]]
## Description 
In java an Array is a static data structure and we can define the size of this array on at the time of creation. We access the elements using an array indices.
This exception occurs when we access an array or a collection that is backed by an array with an invalid index.
### Example
```java
int[] numbers = new int[] {1, 2, 3, 4, 5};
int lastNumber = numbers[5]; // here we can see the ArrayIndexOutOfBoundException
// because the indices of our array is: 0, 1, 2, 3, 4 (we start on 0 in programming)
```