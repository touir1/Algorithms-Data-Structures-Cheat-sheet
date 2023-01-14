# LinkedList datastructure Cheat Sheet (Java)

Some key points:

- A LinkedList has a dynamic size.
- All elements are linked one after the other so getting an element at a certain index requires going throught the elements one by one.

## Declaration

```java
LinkedList<Integer> list;
// or if you want to use the interface List 
// as the LinkedList implements it
List<Integer> list;
```

## Initialization

```java
list = new LinkedList<Integer>();

// to initialize with a predefined size and value
list = new LinkedList<Integer>(Collections.nCopies(10, 0));
// or if just for predefined size
list = new LinkedList<Integer>(Arrays.asList(new Integer[10]));
// or if predefined values
list = new LinkedList<Integer>(Arrays.asList(1,2,3));

// to fill with a specific value
Collections.fill(list,5);
```
