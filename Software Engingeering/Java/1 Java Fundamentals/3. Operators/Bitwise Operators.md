Tags:

- [[Operators summary]]
- [[Java]]
## Description 
Bitwise operators work on binary digits or bits of input values. We can apply these to the integer types –  long, int, short, char, and byte.
Bitwise operators work on a binary equivalent of decimal numbers and perform operations on them bit by bit as per the given operator:
- First, the operands are converted to their binary representation
- Next, the operator is applied to each binary number and the result is calculated
- Finally, the result is converted back to its decimal representation

## Bitwise Logical Operators

The bitwise logical operators are AND(&), OR(|), XOR(^), and NOT(~).

### OR (|)

The OR operator compares each binary digit of two integers and gives back 1 if either of them is 1.

#### Example
```java
int value1 = 6;
int value2 = 5;

// applying bitwise OR operator
int result = 6 | 5;

/** 
To perform this operation, first, the binary representation of these
numbers will be calculated

Binary number of value1 = 0110
Binary number of value2 = 0101

Then the operation will be applied to each bit. The result returns a new binary number:

		0110 
		0101 
		----- 
		0111

Finally, the result 0111 will be converted back to decimal which is equal 
to 7
**/

System.out.println("result: " + result); // Output :> result: 7
```

### AND (&)

The AND operator compares each binary digit of two integers and gives back 1 if both are 1, otherwise it returns 0.
This is similar to the && operator with boolean values. When the values of two booleans are true the result of a && operation is true.

#### Example 
```java
int value1 = 6;
int value2 = 5;

// applying bitwise AND operator
int result = 6 & 5;

/** 
Then the operation will be applied to each bit. The result returns a new binary number:

		0110 
		0101 
		----- 
		0100
		
Finally, the result 0111 will be converted back to decimal which is equal 
to 4
**/

System.out.println("result: " + result); // Output :> result: 4
```

### XOR (^)

The XOR operator compares each binary digit of two integers and gives back 1 if both the compared bits are different. This means that if bits of both the integers are 1 or 0 the result will be 0; otherwise, the result will be 1:

#### Example
```java
int value1 = 6;
int value2 = 5;

// applying bitwise XOR operator
int result = 6 ^ 5;

/** 
Then the operation will be applied to each bit. The result returns a new binary number:

		0110 
		0101 
		----- 
		0011
		
Finally, the result 0111 will be converted back to decimal which is equal 
to 3
**/

System.out.println("result: " + result); // Output :> result: 3
```

### COMPLEMENT (~)
Bitwise Not or Complement operator simply means the negation of each bit of the input value. It takes only one integer and it’s equivalent to the ! operator.
This operator changes each binary digit of the integer, which means all 0 become 1 and all 1 become 0. The ! operator works similarly for boolean values: it reverses boolean values from true to false and vice versa

#### Example 
```java
int value1 = 6;

// applying bitwise Complement operator
int result = ~value1;

/** 
The value binary is: 
value1 = 0000 0110

Applying the complement operator, the result will be:
0000 0110 -> 1111 1001

This is the one’s complement of the decimal number 6. And since the first (leftmost) bit is 1 in binary, it means that the sign is negative for the number that is stored.
Now, since the numbers are stored as 2’s complement, first we need to find its 2’s complement and then convert the resultant binary number into a decimal number:

1111 1001 -> 0000 0110 + 1 -> 0000 0111

Finally, 0000 0111 is 7 in decimal. Since the sign bit was 1 as mentioned above, therefore the resulting answer is -7
**/

System.out.println("result: " + result); // Output :> result: -7
```

### Signed Left Shift (<<)
The left shift operator shifts the bits to the left by the number of times specified by the right side of the operand. After the left shift, the empty space in the right is filled with 0.

#### Example 
```java
int value1 = 12; //  1100

int leftShift = value << 2; // 1100 > 110000

// the value int of 110000 is 48
System.out.println("leftShift: " + leftShift); // leftShift :> result: 48
```

### Signed Right Shift (>>)

**The right shift operator shifts all the bits to the right.** The empty space in the left side is filled depending on the input number:

- **When an input number is negative, where the leftmost bit is 1, then the empty spaces will be filled with 1**
- **When an input number is positive, where the leftmost bit is 0, then the empty spaces will be filled with 0**

#### Example 
```java
int value1 = 12; //  1100

int rightShift = value >> 2; // 1100 > 0011

// the value int of 0011 is 3
System.out.println("rightShift: " + rightShift); // rightShift :> result: 3
```
### Unsigned Right Shift (>>>)
This operator is very similar to the signed right shift operator. The only difference is that the empty spaces in the left are filled with 0 irrespective of whether the number is positive or negative. Therefore, the result will always be a positive integer.

#### Example 
```java
// Example a)
int value1 = 12; //  1100
// 1100 > 0011: the value int of 0011 is 3
int unsignedRightShift = value >>> 2;
// rightShift :> result: 3
System.out.println("unsignedRightShift: " + unsignedRightShift);

// Example b)
int value = -12;
int unsignedRightShift = value >>> 2;

// 1073741821
System.out.println("unsignedRightShift: " + unsignedRightShift);

```
