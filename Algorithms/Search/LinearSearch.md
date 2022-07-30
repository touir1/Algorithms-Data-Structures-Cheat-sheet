# Linear search cheat sheet (Java)

The linear search algorithm is the most intuitive one.

To find an element in an array, you iterate through all the list from index 0 to index N-1 and check each time if the element in that index corresponds to the searched element.

![](https://github.com/touir1/Algorithms-Data-Structures-Cheat-sheet/blob/main/Algorithms/Search/Images/Linear_search_animation.gif)

He's the code for the search algorithm:

```java
int[] array = new int[] {6,8,3,4,2,5,8,11};
int element = 5;
		
// we're looking for the element 5 in the array
int found = -1;
		
// looping through all the array, if the element is found, we exit the loop
for (int i=0;i < array.length; i++) {
	if(array[i] == element) {
		found = i;
		break;
	}
}
		
// check if the element is found
if(found != -1)
	System.out.println("Element found at index: "+ found);
else
	System.out.println("Element was not found");
```

Please note that the algorithm doesn't need the list to be sorted or the element to be in a certain order.

For the complexities:

- Time complexity: O(N) as we're looping through all the element in the array (worst case) to find the element

- Space complexity: O(1) as we don't need extra space for the algorithm



Function implementation:

```java
public static int search(int[] array, int length, int element) {
	for(int i=0;i< length; i++) {
		if(array[i] == element)
			return i;
	}
	return -1;
}
```
