# Bitmask cheat sheet (Java)

Some key points:

- Small set of booleans

- Stored in integer type as it's a sequence of bit in memory

- Quicker than an array of boolean as it uses bitwise operations

## Bitwise operations

### Initialization

```java
// initialization
// represented by a simple integer
int bitmask = 0;
```

### Shift left (<<)

The left shift operation moves all the bits to the left n times

```java
// shift all bits to the left 2 times
// 011 (3) becomes 110 (5)
bitmask = (3 << 2);
```

### Shift right (>>)

The right shift operation moves all the bits to the right n times

```java
// shift all bits to the right 2 times
// 101 (4) becomes 10 (2)
bitmask = (5 >> 2);
```

### OR operator (|)

The or operation between two bits sets 1 if one of them  (or both) have the value 1

```java
// 1010 (10) or
// 1001 ( 9)
// --------- =
// 1011 (11)
bitmask = 10 | 9; // 11

// the OR operation can be used directly on the variable
bitmask |= 4; // 15
```

### AND operation (&)

The and operation between two bits sets 1 if both of them have the value 1

```java
// 1010 (10) and
// 1001 ( 9)
// --------- =
// 1000 ( 8)
bitmask = 10 & 9; // 8

// the AND operation can be used directly on the variable
bitmask &= 1; // 0
```

### NOT / 1's complement operation (~)

The NOT operation is a unary operator that reverses all the bits of a variable

```java
// ~ 00000000 00000000 00000000 00000101 
// ------------------------------------- =
//   11111111 11111111 11111111 11111010
bitmask = ~5; // -6 (1's complement)
```

Please note that the negative numbers in java are stored as 2's complement of their positive counterpart.

For example if we want the negative value of the number 2:

- number 2 = 00000000 00000000 00000000 00000010 in binary

- First we get the 1's complement by reversing all the bits which gives
  
  11111111 11111111 11111111 11111101

- Then, we add 1 to the 1's complement which gives:
  
  11111111 11111111 11111111 11111110
  
  which equals to -2 in java (2's complement of 2).

Another way to have the 2's complement is as follows:

- find the least significant bit (LSB for short) from the right which is on (first bit with value 1 from the right)

- reverse all the bits from its left

So if we take the number 2 as example:

- 2 = 00000000 00000000 00000000 00000010 so the LSB is the 2nd bit

- we reverse all the bits on the left of the 2nd bit, that gives:
  
  11111111 11111111 11111111 11111110

### XOR operation (^)

The XOR operation between 2 bits gives 1 if both of them are different and 0 otherwise.

```java
// 1100 (12) XOR
// 1010 (10)
// ----------- =
// 0110 ( 6)
bitmask = (12 ^ 10); // 6

// the XOR operation can be used directly on the variable
bitmask ^= 2; // 4
```

## Usage

### Multiply or divide by 2

Multiplying or dividing by 2 is done via the shift operations. As it moves all the bits to the left (multiplying by 2) or to the right (dividing by 2).

```java
// dividing by 2
bitmask = (5 >> 2); // 2

// multiplying by 2
bitmask = (4 << 2); // 8
```

### Set / turn on the i-th bit

To do that, we use the OR operation with a shift to the left of 1 (i-1) times.

```java
// 1000 (8) OR
// 0010 (2) => (1 << 2)
// -------- =
// 1010 (10)
bitmask = 8 | (1 << 2); // 10
// or
bitmask |= (1 << 2); // 10 if bitmask initial value is 8
```

### Check if i-th bit is on

To check if the i-th bit is on, we need to use the AND operation with a shift to the left of 1 (i-1) times.

If the resulting value is 0 then the bit is off. The bit is on otherwise (it's value is equal to (1 << (i-1)).

```java
// check if the 2nd bit is on
// 1101 (13) AND
// 0010 ( 2) => (1 << 2)
// ---------- =
// 0000 ( 0) => 2nd bit is off
bitmask = 13 & (1 << 2); // 0
// check if the 2nd bit is on
// 1110 (14) AND
// 0010 ( 2) => (1 << 2)
// ---------- =
// 0010 ( 2) => 2nd bit is on
bitmask = 13 & (1 << 2); // 2

// so the check would be
if(bitmask & (1 << (i-1)) != 0) { // if i-th bit is on

}
```

### Clear / turn off the i-th bit

To clear the i-th bit, we use the AND operation combined with an integer with all bits to 1 except the one we want to check.

To get that, we use the NOT operation (2's complement) combined with a shift to the left (i-1) times.

```java
// turn off the 5th bit
// 00000000 00000000 00000000 00010101 ( 21) AND
// 11111111 11111111 11111111 11101111 (-17) => ~(1 << (i-1))
//                                              ~(1 << 4)
// ------------------------------------------- =
// 00000000 00000000 00000000 00000101 (  5)
bitmask &= ~(1 << (i-1));
```

### Toggle / reverse the i-th bit

To do that, we use the XOR operation with a shift to the left (i-1) times. 

XOR will reverse the value using the shifted 1 at that position as 1 XOR 1 = 0 and 0 XOR 1 = 1;

As  for the other bits:

- if the initial value of the bits that we don't want to touch are 0, the XOR with the shifted 1 isn't going to change that as 0 XOR 0 gives 0.

- same logic for the values 1, as 1 XOR 0 gives 1.

```java
// reverse the 3rd bit
// 1011 (11) XOR
// 0100 ( 4) => (1 << 2)
// ----------- =
// 1111 ( 15)
bitmask ^= (1 << (i-1));
```

### Value of least significant bit (LSB) that is on (first from the right)

The least significant bit that is on is the first bit that have the value 1 going from the right.

As an example, for the case of 1100 (12), the corresponding value is 8 (3rd bit from the right).

To get that, we use AND operation between the bitmask and its 2's complement (negative representation of the value).

Explanation:

- The 2's complement of a value in binary is represented by having all the bits on the left of the LSB reversed (see explanation in the NOT bitwise operation part)

- If we do an AND operation between a number and its 2's complement (negative representation), we get the LSB as it's the only value that is on (value 1) on both parts (number and its negative representation).

```java
// 00000000 00000000 00000000 00010100 ( 20) AND
// 11111111 11111111 11111111 11101100 (-20) => 2's complement
// ------------------------------------------- =
// 00000000 00000000 00000000 00000100 (  4) => LSB
bitmask = 20; // initialization
int lsb = bitmask & (-bitmask); // 4
```

### Turn on all bits in a set of size n

To turn on all bits in a set of size in, we just need to shift 1 n times and remove 1.

Beware of overflows, as setting for example all the bits of an integer (32 bits) to 1 using this method will overflow with the shift bitwise operation.

```java
// we need 5 bits to 1 representing the value 63
// 100000 ( 64) => (1 << 5)
// we then remove 1 so we have
// 011111 ( 63)
bitmask = (1 << 5) -1;
```

### Check if number is power of 2

To check if a number is a power of two we use LSB to get the first bit which is on from the right and check if the result corresponds to the first number.

```java
int number = 8; // 00001000
// LSB(00001000) = 00001000 & 11111111 11111111 11111111 11111000 = 00001000
// 8 (00001000) == 8 (00001000)
boolean result = (number & (-number)) == number; // true
number = 7; // 00000111
// LSB(00000111) = 00000111 & 11111111 11111111 11111111 11111001 = 00000001
// 7 (00000111) != 1 (00000001)
result = (number & (-number)) == number; // false
```
