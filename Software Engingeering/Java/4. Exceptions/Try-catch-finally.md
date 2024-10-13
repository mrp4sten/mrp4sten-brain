Tags:
- [[Java]]
- [[Exceptions]]
- [[Common Exceptions]]
## Description
Exceptions are Java objects extending from `Throwable` 
```
              ---> Throwable <--- 
              |    (checked)     |
              |                  |
              |                  |
      ---> Exception           Error
      |    (checked)        (unchecked)
      |
RuntimeException
  (unchecked)
```
We have 3 categories of exceptional conditions
- Checked exceptions 
- Unchecked exceptions / Runtime exceptions  
- Errors
> See more on [[Checked and unchecked exceptions]]

The statement `try-catch-finally` allow catch and manage the exceptions basically. consider that the `finally` statement allow run our code regardless if any error occur so if we can run code include if any error occur we should to use finally block
### Example
```java
public int getPlayerScore(String playerFile) {
    try {
        Scanner contents = new Scanner(new File(playerFile));
        return Integer.parseInt(contents.nextLine());
    } catch (FileNotFoundException noFile) {
        throw new IllegalArgumentException("File not found");
    }
}
```

```java
public int getPlayerScore(String playerFile)
  throws FileNotFoundException {
    Scanner contents = null;
    try {
        contents = new Scanner(new File(playerFile));
        return Integer.parseInt(contents.nextLine());
    } finally {
        if (contents != null) {
            contents.close();
        }
    }
}

```
``