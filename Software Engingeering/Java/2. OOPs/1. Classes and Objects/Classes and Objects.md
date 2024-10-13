Tags: 
- [[Java]]
## Classes
Simply put, a class represent a definition or a type of object. In Java, classes can contain fields, constructors, and methods.

### Example
```java
class Car {
    // fields
    String type;
    String model;
    String color;
    int speed;
    // constructor
    Car(String type, String model, String color) {
        this.type = type;
        this.model = model;
        this.color = color;
    }
    // methods
    int increaseSpeed(int increment) {
        this.speed = this.speed + increment;
        return this.speed;
    }
}
```

This Java class represents a car in general. We can create any type of car from this class. We use fields to hold the state and a constructor to create objects from this class.
Every Java class has an empty constructor by default. We use it if we don’t provide a specific implementation as we did above.

## Objects
While classes are translated during compile time, objects are created from classes at runtime.
Objects of a class are called instances, and we create and initialize them with constructors:

```java

// Car creation (if the constructor is not implemented, the params is not used to create a new car)
Car focus = new Car("Ford", "Focus", "red");
Car auris = new Car("Toyota", "Auris", "blue");
Car golf = new Car("Volkswagen", "Golf", "green");

// each car type change the speed
focus.increaseSpeed(10);
auris.increaseSpeed(20);
golf.increaseSpeed(30);
```

> Note: Every field and method in our class should’ve also defined access control by a specific modifier. Classes usually have public modifiers, but we tend to keep our fields private. Fields hold the state of our object, therefore we want to control access to that state. We can keep some of them private, and others public. We achieve this with specific methods called getters and setters. 

#### Getters and Setters quick example (this is basically Encapsulation):

```java
public class Car {
    private String type;
    // ...

    public Car(String type, String model, String color) {
       // ...
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }

    public int getSpeed() {
        return speed;
    }

    // ...
}
```

