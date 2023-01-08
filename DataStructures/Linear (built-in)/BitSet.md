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

Bibliography:
- [Guide to BitSet in Java - Baeldung](https://www.baeldung.com/java-bitset)
