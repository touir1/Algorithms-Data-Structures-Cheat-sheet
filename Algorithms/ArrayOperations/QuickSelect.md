# Quick Select Algorithm (Java)

```java
public static int partition(int[] arr, int left, int right, int pivot) {
	int pivotValue = arr[pivot];
	swap(arr, pivot, right); // move pivot to end
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
	if(left == right) {
		return arr[left];
	}
	
	while(true) {
		int pivotIndex = (left + right) / 2;
		pivotIndex = partition(arr, left, right, pivotIndex);
		
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

Bibliography:

- [Quickselect Algorithm - GeeksforGeeks](https://www.geeksforgeeks.org/quickselect-algorithm/)
- [A basic implementation of quickselect algorithm in Java. Intentionally unused generics.](https://gist.github.com/unnikked/14c19ba13f6a4bfd00a3)
