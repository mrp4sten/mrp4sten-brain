Tags:
- [[Java]]

## Description

In Java, an operator is a special symbol or keyword used to perform operations on variables and values. Operators are fundamental to manipulating data and creating expressions in Java.

### Example code summary
```java
public class OperatorsExample {
    public static void main(String[] args) {
        // Arithmetic Operators
        int a = 10;
        int b = 5;
        int sum = a + b;       // Addition
        int difference = a - b; // Subtraction
        int product = a * b;    // Multiplication
        int quotient = a / b;   // Division
        int remainder = a % b;  // Modulus
        int increment = ++a;    // Increment
        int decrement = --b;    // Decrement

        // Relational Operators
        boolean isEqual = (a == b);     // Equal to
        boolean isNotEqual = (a != b);  // Not equal to
        boolean isGreater = (a > b);    // Greater than
        boolean isLess = (a < b);       // Less than
        boolean isGreaterOrEqual = (a >= b); // Greater than or equal to
        boolean isLessOrEqual = (a <= b);    // Less than or equal to

        // Logical Operators
        boolean logicalAnd = (a > 0 && b > 0);  // Logical AND
        boolean logicalOr = (a > 0 || b < 0);   // Logical OR
        boolean logicalNot = !(a > b);          // Logical NOT

        // Bitwise Operators
        // This is most advanced operators (is used for unix permissioins, data copmpression, cryptography and security, graphics programming, networking programming, Finite State Machines and Flags, Low-Level Device Control, Hamming Code))
        int bitwiseAnd = a & b;  // Bitwise AND
        int bitwiseOr = a | b;   // Bitwise OR
        int bitwiseXor = a ^ b;  // Bitwise XOR
        int bitwiseNot = ~a;     // Bitwise NOT
        int leftShift = a << 2;  // Left shift
        int rightShift = a >> 2; // Right shift
        int unsignedRightShift = a >>> 2; // Unsigned right shift

        // Assignment Operators
        int c = 10;
        c += 5;  // Equivalent to c = c + 5;
        c -= 3;  // Equivalent to c = c - 3;
        c *= 2;  // Equivalent to c = c * 2;
        c /= 2;  // Equivalent to c = c / 2;
        c %= 2;  // Equivalent to c = c % 2;

        // Miscellaneous Operators
        int ternaryResult = (a > b) ? a : b;  // Ternary operator
        String str = (a > b) ? "a is greater" : "b is greater"; // Ternary with String

        // Typecasting Operator
        double d = 9.78;
        int castedInt = (int) d;  // Explicit casting from double to int
    }
}

```