Tags: 
- [[Java]]
- [[OOP]]
## Description
Displays only the relevant attributes and hide the unnecessary details e.g. when we are playing any video game we just wants to know how to play, we don't wants to know how is working exactly the video game internally, which programming language used, how the memory save our match or how we can play with players from different kind of places. 

## Example code
```java
//abstract class
abstract class Car{
    abstract void accelerate();
}

//concrete class`
class Suzuki extends Car{
    void accelerate(){
        System.out.println("Suzuki::accelerate");
    }
}

class Main{
    public static void main(String args[]){
        Car obj = new Suzuki();//Car object =>contents of Suzuki`
        obj.accelerate();//call the method` 
    }  
}
```