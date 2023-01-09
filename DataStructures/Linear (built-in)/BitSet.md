# BitSet cheat sheet (Java)

Some key points: 

- It represents a sequence of bits using long array internally
  
- Takes less space than an array of boolean as it uses the bits of each long variable of the array
  
- Quick as it uses bitwise operations

## BitSet Constructor

```java
// constructor without parameters
BitSet bitSet = new BitSet();
// the parameter represents the initial size (number of bits)
BitSet bitSet = new BitSet(100_000);
```

You can also create a BitSet from existing arrays like long[], byte[] or from LongBuffer and ByteBuffer using BitSet valueOf function (different overloads)

```java
// long = 64 bits so an array of two bits represents 128 size BitSet
BitSet bitSet = BitSet.valueOf(new long[] { 42, 12 });
```

## Setting bits

```java
// set the bit at index 10 to true
bitSet.set(10);
// set bits in range [20,30[ to true (fromInclusive, toExclusive)
bitSet.set(20, 30);
// you can also set it to false using the same function
bitSet.set(10, false);
// same for range
bitSet.set(20, 30, false);
```

## Clearing bits

```java
// to clear the bit at position 42 (set it to false)
bitSet.clear(42);
// clear bits in range [20,30[ (fromInclusive, toExclusive)
bitSet.clear(20,30);
// clear all the bitSet
bitSet.clear()
```

## Getting bits

```java
// to get the value of a bit
System.out.println("value of bit at position 42: "+bitSet.get(42));
// you can also get a range of bits, [10,20[ (fromInclusive, toExclusive)
BitSet newBitSet = bitSet.get(10, 20);
```

## Flipping bits

Flipping a bit means to reverse its value, so 1 becomes 0 and vis versa.

```java
bitSet.set(42); // bit 42 is on (true)
// flip its value to false
bitSet.flip(42);
// we can also use the same logic as the other methods to flip a range of values (fromInclusive, toExclusive)
bitSet.flip(10,20);
```

## Size, length, cardinality and isEmpty

The **size()** method returns the **physical size of the bitSet**. So for example, if we have intantiate a bitSet with no arguments passed to the constructor, we'll have a long[] of size 1. Then the size would be 64.  
The **length()** method returns the **logical size of the bitSet**. That means the that the method returns the position of the the bit after the last bit set to true (size of the sub array from the beginning to the last bit set to true).  
The **cardinality()** method returns the **number of bits set to true** in the bitSet.  
The **isEmpty()** method **checks if all the bits are off**. So if we have at least one bit set to true, the method returns false.

```java
// creating a bitset of size 1024
BitSet bitSet = new BitSet(1024);
bitSet.set(5,10); // setting bits from 5 to 10 exclusive to true

System.out.println("size: " + bitSet.size() + ", length: " + bitSet.length() 
       + ", cardinality: " + bitSet.cardinality() + ", isEmpty: " + bitSet.isEmpty());
// output: size: 1024, length: 10, cardinality: 5, isEmpty: false

bitSet.clear(); // clear the bitSet so all the values are set to false

System.out.println("size: " + bitSet.size() + ", length: " + bitSet.length() 
       + ", cardinality: " + bitSet.cardinality() + ", isEmpty: " + bitSet.isEmpty());
// output: size: 1024, length: 0, cardinality: 0, isEmpty: true
```

## Logical operations: and, andNot, or, xor, intersects

```java
BitSet b1 = BitSet.valueOf(new long[]{6});  // 00110
BitSet b2 = BitSet.valueOf(new long[]{10}); // 01010

// and operation between 2 bitSets, the result is put in the first variable (the one calling and())
b1.and(b2); // b1 = 010 (2)

// andNot clears all the bits that are set to true in the corresponding bitSet passed as parameter
// x.andNot(y) is equivalent to x & (~ y) which is equivalent to x and (not y) in logical terms.
b1 = BitSet.valueOf(new long[]{6});
b1.andNot(b2); // result: b1 = 00100

// or operation between 2 bitSets, result is in the first variable
b1.or(b2); // result: b1 = 00100 & 01010 = 01110

// xor operation
b1.xor(b2); // b1 = 01110 ^ 01010 = 00100

// intersects operation returns true if both BitSets have at least 1 bit set to true at the same position.
System.out.println(b1.intersects(b2)); // false
b1 = BitSet.valueOf(new long[]{2});
System.out.println(b1.intersects(b2)); // true
```



Bibliography:
- [Guide to BitSet in Java - Baeldung](https://www.baeldung.com/java-bitset)
