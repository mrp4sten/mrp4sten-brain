Tags: 
- [[Java]]
## Description
In Java, an interface is an abstract type that contains a collection of methods and constant variables. It is one of the core concepts in Java and is used to achieve abstraction, [[Polymorphism]] and multiple [[Inheritance]].

```java
public interface Electronic {

    // Constant variable
    String LED = "LED";

    // Abstract method
    int getElectricityUse();

    // Static method
    static boolean isEnergyEfficient(String electtronicType) {
        if (electtronicType.equals(LED)) {
            return true;
        }
        return false;
    }

    //Default method
    default void printDescription() {
        System.out.println("Electronic Description");
    }
}

```

## Rules
In an interface, we’re allowed to use:

- constant variables
- abstract methods
- static methods
- default methods

We also should remember that:

- we can’t instantiate interfaces directly
- an interface can be empty, with no methods or variables in it
- we can’t use the _final_ word in the interface definition, as it will result in a compiler error
- all interface declarations should have the _public_ or default access modifier; the _abstract_ modifier will be added automatically by the compiler
- an interface method can’t be _protected_ or _final_
- up until Java 9, interface methods could not be _private_; however, Java 9 introduced the possibility to define private method in interfaces
- interface variables are _public_, _static_, and _final_ by definition; we’re not allowed to change their visibility