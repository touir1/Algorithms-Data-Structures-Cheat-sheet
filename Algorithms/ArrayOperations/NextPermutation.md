# Next Permutation Algorithm (Java)

```java
public static boolean nextPermutation(char[] arr) {
		
	// no permutations for size < 2
	if(arr.length <= 1) return false;
	
	int pivot = arr.length - 1;
	
	// find the longest non-increasing suffix
	// the pivot would be the starting index of that suffix
	while(--pivot >= 0 && arr[pivot] >= arr[pivot + 1]);
	
	// if no increasing pair, no permutation possible
	if(pivot < 0) return false;
	
	int successor = arr.length;
	
	// find the successor of the pivot
	// rightmost element greater than the pivot
	while(--successor > pivot && arr[successor] <= arr[pivot]);
	
	// swap the pivot and the successor
	arr = swap(arr,pivot,successor);
	
	// reverse the suffix
	arr = reverse(arr, pivot + 1, arr.length - 1);
	
	return true;
}
```

More information:

- [Swap algorithm](Swap.md)

- [Reverse algorithm](Reverse.md)

Bibliography:

- [Implementing next_permutation() in Java with Examples - GeeksforGeeks](https://www.geeksforgeeks.org/implementing-next_permutation-in-java-with-examples/)
