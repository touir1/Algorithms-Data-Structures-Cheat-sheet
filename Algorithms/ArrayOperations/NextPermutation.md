# Next Permutation Algorithm (Java)

The next permutation algorithm is an algorithm that generates the next lexicographically larger permutation of a given sequence. It is often used in combinatorial algorithms where it is necessary to generate all the permutations of a sequence in a particular order.

The algorithm works by first finding the largest index i such that the sequence is not in descending order at that index, that is, the element at index i-1 is smaller than the element at index i. 

If no such index exists, then the sequence is already the largest permutation and the algorithm terminates. 

Otherwise, the algorithm searches for the smallest element in the sequence that is larger than the element at index i-1 and swaps these two elements. 

Finally, the algorithm reverses the sub-sequence starting at index i, as this sub-sequence is now in descending order and needs to be reversed to get the next lexicographically larger permutation.

| Time Complexity | Space Complexity |
| --------------- | ---------------- |
| O(N)            | O(1)             |

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
