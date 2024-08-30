Tags:
- [[SOLID]]
- [[Design Patterns]]
- [[Design Principles]]
- [[Programming]]
## Description
If class A is a sub type of class B, we should be able to replace B with A without disrupting the behavior of our program

### Sample without Liskov Substitution
```java
// Base class
public class Rectangle {
    protected int width;
    protected int height;
    
    public void setWidth(int width) {
        this.width = width;
    }
    
    public void setHeight(int height) {
        this.height = height;
    }
    
    public int getWidth() {
        return width;
    }
    
    public int getHeight() {
        return height;
    }
    
    public int calculateArea() {
        return width * height;
    }
}

// Subclass that violates LSP
public class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        this.width = width;
        this.height = width; // Ensure width and height are always the same
    }
    
    @Override
    public void setHeight(int height) {
        this.height = height;
        this.width = height; // Ensure width and height are always the same
    }
}
```
### With Liskov Substitution
```java
// Base class
public abstract class Shape {
    public abstract int calculateArea();
}

// Rectangle class
public class Rectangle extends Shape {
    protected int width;
    protected int height;
    
    public void setWidth(int width) {
        this.width = width;
    }
    
    public void setHeight(int height) {
        this.height = height;
    }
    
    public int getWidth() {
        return width;
    }
    
    public int getHeight() {
        return height;
    }
    
    @Override
    public int calculateArea() {
        return width * height;
    }
}

// Square class
public class Square extends Shape {
    private int side;
    
    public void setSide(int side) {
        this.side = side;
    }
    
    public int getSide() {
        return side;
    }
    
    @Override
    public int calculateArea() {
        return side * side;
    }
}

```