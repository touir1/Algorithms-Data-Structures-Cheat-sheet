# Quick Select Algorithm (Java)

The Quick Select is an algorithm for finding the kth smallest element in an unordered list. It is similar to [Quicksort](../Sort/QuickSort.md), but instead of recursively sorting both sublists, it only recursively sorts the sublist containing the desired element.

| Time Complexity | Space Complexity |
| --------------- | ---------------- |
| O(N^2)          | O(1)             |

```java
/*
* The partition function is a subprocedure of Quick Sort that is used to split the list in
* two groups, the first consisting of elements that are less than the value of the pivot and the second
* is greater than the value of the pivot.
* It has a linear complexity of O(N) in case when left is the zero index and right is the
* end of the array
*/
public static int partition(int[] arr, int left, int right, int pivot) {
	int pivotValue = arr[pivot];
	swap(arr, pivot, right); // move pivot to the end of the array
	int storeIndex = left;
	for(int i = left; i < right; i++) {
		if(arr[i] < pivotValue) {
			swap(arr, storeIndex, i);
			storeIndex++;
		}
	}
	swap(arr, right, storeIndex); // Move pivot to its final place
	return storeIndex;
}	

public static int quickSelect(int[] arr, int left, int right, int n) {
	if(left == right) { // size of sub array is 1 so the kth element has only one value
		return arr[left];
	}
	
	// iterative approch instead of recursively calling quick select
	while(true) {
		// choosing pivot as the half point but it's a choice you can choose whatever
		// index.
		int pivotIndex = (left + right) / 2;
		// get the index of the new pivot after splitting the array in two groups (less
		// and greater than the pivot value)
		pivotIndex = partition(arr, left, right, pivotIndex);
		
		// check if we found the kth smallest element
		if(n == pivotIndex) {
			return arr[n];
		} else if(n < pivotIndex) {
			right = pivotIndex - 1;
		} else {
			left = pivotIndex + 1;
		}
	}
}
```

More information:

- [Swap algorithm](Swap.md)
- [Quicksort algorithm](../Sort/QuickSort.md)

Bibliography:

- [Quickselect Algorithm - GeeksforGeeks](https://www.geeksforgeeks.org/quickselect-algorithm/)
- [A basic implementation of quickselect algorithm in Java. Intentionally unused generics.](https://gist.github.com/unnikked/14c19ba13f6a4bfd00a3) (thank you [@unnikked](https://github.com/unnikked) for the gist and explanation)

