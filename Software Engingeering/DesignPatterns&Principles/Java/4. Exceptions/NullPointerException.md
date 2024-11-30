Tags:
- [[Java]]
- [[Exceptions]]
- [[Common Exceptions]]
## Description
Is a runtime exception. In java, a special null value can be assigned to an object reference.
This exception is thrown when a program attempts to use  an object reference that has the null value.
### Some reasons
- Invoking a method from a null object.
- Accessing or modifying a null object’s field.
- Taking the length of null, as if it were an array.
- Accessing or modifying the slots of null objects, as if it were an array.
- Throwing null, as if it were a Throwable value.
- When you try to synchronize over a null object.