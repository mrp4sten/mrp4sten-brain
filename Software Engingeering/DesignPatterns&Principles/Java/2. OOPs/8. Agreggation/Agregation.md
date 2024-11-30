Tags: 
- [[Java]]
- [[OOP]]

## Description

If a class have an entity reference, it is known as Aggregation. Aggregation represents **HAS-A** relationship

![[aggregation.JPG]]

## Code example
```java
class Employee{  
	int id;  
    String name;  
    Address address;//Address is a class  
}  
```
 in this example Employee has an entity reference address, so relationship is **Employee HAS-A Address**
