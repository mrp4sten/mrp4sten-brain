Tags: 
- [[Java]]
- [[OOP]]

## Description

Prevent other classes from accessing or changing field or methods of a classes. This helps to achieve data hiding.  
This concept help us to keep related fields and methods together, control the values of our data fields, with getters and setters we can control the read-only or write-only of our data fields, 

## Example

```java
class Area {

  // fields to calculate area
  int length;
  int breadth;

  // constructor to initialize values
  Area(int length, int breadth) {
    this.length = length;
    this.breadth = breadth;
  }

  // method to calculate area
  public void getArea() {
    int area = length * breadth;
    System.out.println("Area: " + area);
  }
}

class Main {
  public static void main(String[] args) {

    // create object of Area
    // pass value of length and breadth
    Area rectangle = new Area(5, 6);
    rectangle.getArea();
  }
}
```