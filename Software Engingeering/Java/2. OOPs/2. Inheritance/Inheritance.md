Tags: 
- [[Java]]
- [[OOP]]

## Description
One of the core principles of Object-Oriented Programming – inheritance – enables us to reuse existing code or extend an existing type.
Simply put, in Java, a class can inherit another class and multiple interfaces, while an interface can inherit other interfaces.

![[inheritance.png]]

```java
public class Car {
    int wheels;
    String model;
    void start() {
        // Check essential parts
    }
}

public class ArmoredCar extends Car {
    int bulletProofWindows;
    void remoteStartCar() {
	// this vehicle can be started by using a remote control
    }
}
```
We can now say that the ArmoredCar class is a subclass of Car, and the latter is a superclass of ArmoredCar.

> Classes in Java support single inheritance; the ArmoredCar class can’t extend multiple classes. Also, note that in the absence of an extends keyword, a class implicitly inherits class java.lang.Object.

> A subclass class inherits the non-static protected and public members from the superclass class. In addition, the members with default (package-private) access are inherited if the two classes are in the same package.

## Accessing Parent Members from a Child Class

To access inherited properties or methods, we can simply use them directly:
```java
public class ArmoredCar extends Car {
    public String registerModel() {
        return model;
    }
}
```

## [[Interface]] inheritance

Although classes can inherit only one class, they can implement multiple interfaces.
```java
public interface Floatable {
    void floatOnWater();
}

public interface Flyable {
    void fly();
}

public class ArmoredCar extends Car implements Floatable, Flyable{
    public void floatOnWater() {
        System.out.println("I can float!");
    }
 
    public void fly() {
        System.out.println("I can fly!");
    }
}
```

## Interfaces Extending Other Interfaces
```java
public interface Floatable {
    void floatOnWater();
}

interface interface Flyable {
    void fly();
}

public interface SpaceTraveller extends Floatable, Flyable {
    void remoteControl();
}
```

## Inheriting Type

When a class inherits another class or interfaces, apart from inheriting their members, it also inherits their type. This also applies to an interface that inherits other interfaces.

This is a very powerful concept, which allows developers to program to an interface (base class or interface), rather than programming to their implementations.

```java
public class Employee {
    private String name;
    private Car car;
    
    // standard constructor
}

Employee e1 = new Employee("Shreya", new ArmoredCar());
Employee e2 = new Employee("Paul", new SpaceCar());
Employee e3 = new Employee("Pavni", new BMW());
```

## Hidden Class Members

### Hidden Instance Members
What happens if both the superclass and subclass define a variable or method with the same name? Don’t worry; we can still access both of them. However, we must make our intent clear to Java, by prefixing the variable or method with the keywords this or super.

```java
public class ArmoredCar extends Car {
    private String model;
    public String getAValue() {
    	return super.model;   // returns value of model defined in base class Car
    	// return this.model;   // will return value of model defined in ArmoredCar
    	// return model;   // will return value of model defined in ArmoredCar
    }
}
```

### Hidden Static Members
What happens when our base class and subclasses define static variables and methods with the same name? Can we access a static member from the base class, in the derived class, the way we do for the instance variables?
No, we can’t. The static members belong to a class and not to instances. So we can’t use the non-static super keyword in msg().

```java
public class Car {
    public static String msg() {
        return "Car";
    }
}

public class ArmoredCar extends Car {
    public static String msg() {
        // return super.msg(); this won't compile.
        return Car.msg(); // this works!
    }
}
```

```java
public class Car {
    public static String msg() {
        return "Car";
    }
}

public class ArmoredCar extends Car {
    public static String msg() {
        return "ArmoredCar";
    }
}

Car first = new ArmoredCar();
ArmoredCar second = new ArmoredCar();
```