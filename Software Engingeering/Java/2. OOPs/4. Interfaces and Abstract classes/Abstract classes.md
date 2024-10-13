Tags: 
- [[Java]]
## Description

An abstract class in Java is a class that cannot be instantiated on its own and is meant to be subclassed by other classes. It serves as a blueprint for other classes and may include abstract methods, which are methods declared without an implementation. The subclasses of the abstract class are required to provide implementations for these abstract methods.

```java
abstract class Animal {
    abstract void makeSound();

    void eat() {
        System.out.println("This animal is eating.");
    }
}


class Dog extends Animal {
    Dog(String name) {
        super(name);
    }
    
    @Override
    void makeSound() {
        System.out.println("Bark");
    }
}

```