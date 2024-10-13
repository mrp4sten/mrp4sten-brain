Tags: 
- [[Java]]
- [[OOP]]

## Static Polymorphism
Static polymorphism is an imitation of polymorphism which is resolved at compile time and thus does away with run-time virtual-table lookups.

```java
public class TextFile extends GenericFile {
    //...

    public String read() {
        return this.getContent()
          .toString();
    }

    public String read(int limit) {
        return this.getContent()
          .toString()
          .substring(0, limit);
    }

    public String read(int start, int stop) {
        return this.getContent()
          .toString()
          .substring(start, stop);
    }
}
```

## Dynamic Polymorphism

With dynamic polymorphism, the Java Virtual Machine (JVM) handles the detection of the appropriate method to execute when a subclass is assigned to its parent form. This is necessary because the subclass may override some or all of the methods defined in the parent class.

```java
public class GenericFile {
    private String name;

    //...

    public String getFileInfo() {
        return "Generic File Impl";
    }
}

public class ImageFile extends GenericFile {
    private int height;
    private int width;

    //... getters and setters
    
    public String getFileInfo() {
        return "Image File Impl";
    }
}

public static void main(String[] args) {
    GenericFile genericFile = new ImageFile("SampleImageFile", 200, 100, 
      new BufferedImage(100, 200, BufferedImage.TYPE_INT_RGB)
      .toString()
      .getBytes(), "v1.0.0");
    logger.info("File Info: \n" + genericFile.getFileInfo());
}

// Output :> File Info: Image File Impl
```

## Coercion

Polymorphic coercion deals with implicit type conversion done by the compiler to prevent type errors. A typical example is seen in an integer and string concatenation:

```java
String str = “string” + 2;
```

## Operator Overloading

Operator or method overloading refers to a polymorphic characteristic of same symbol or operator having different meanings (forms) depending on the context.

```java
String str = "2" + 2;
int sum = 2 + 2;
System.out.printf(" str = %s\n sum = %d\n", str, sum);

/**
Output:> 
	str = 22 
	sum = 4
**/
```

## Polymorphic Parameters
Parametric polymorphism allows a name of a parameter or method in a class to be associated with different types. We have a typical example below where we define content as a String and later as an Integer:

```java
public class TextFile extends GenericFile {
    private String content;
    
    public String setContentDelimiter() {
        int content = 100;
        this.content = this.content + content;
    }
}
```
> It’s also important to note that declaration of polymorphic parameters can lead to a problem known as variable hiding where a local declaration of a parameter always overrides the global declaration of another parameter with the same name.

> To solve this problem, it is often advisable to use global references such as this keyword to point to global variables within a local context.