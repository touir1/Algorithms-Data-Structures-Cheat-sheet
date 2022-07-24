# Bitmask cheat sheet (Java)

Some key points:

- Small set of booleans

- Stored in integer type as it's a sequence of bit in memory

- Quicker than an array of boolean as it uses bitwise operations

## Operations

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
```

### AND operation (&)

The and operation between two bits sets 1 if both of them have the value 1

```java
// 1010 (10) and
// 1001 ( 9)
// --------- =
// 1000 ( 8)
bitmask = 10 & 9; // 8
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

### XOR operation (^)

The XOR operation between 2 bits gives 1 if both of them are different and 0 otherwise.

```java
// 1100 (12) XOR
// 1010 (10)
// ----------- =
// 0110 ( 6)
bitwise = (12 ^ 10); // 6
```

# 
