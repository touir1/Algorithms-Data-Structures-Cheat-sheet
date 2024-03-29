# Algorithms cheat cheet (Java)

In here, you'll find a list of many interesting algorithms with some explanation, key points and time / space complexity.

## Sort algorithms

| Algorithm                                         | Time complexity                                 | Space complexity |
| ------------------------------------------------- | ----------------------------------------------- | ---------------- |
| Bubble sort ([details](Sort/BubbleSort.md))       | O(N²)                                           | O(1)             |
| Selection sort ([details](Sort/SelectionSort.md)) | O(N²)                                           | O(1)             |
| Insertion sort ([details](Sort/InsertionSort.md)) | O(N²)                                           | O(1)             |
| Merge sort ([details](Sort/MergeSort.md))         | O(N log N)                                      | O(N)             |
| Heap sort ([details](Sort/HeapSort.md))           | O(N log N)                                      | O(1)             |
| Quick sort ([details](Sort/QuickSort.md))         | O(N log N)                                      | O(N)             |
| Counting sort ([details](Sort/CountingSort.md))   | O(N)                                            | O(N)             |
| Radix sort ([details](Sort/RadixSort.md))         | O(N)                                            | O(N)             |
| Bucket sort ([details](Sort/BucketSort.md))       | O(N log N), depends on bucket sorting algorithm | O(N)             |

## Search algorithms

| Algorithm                                                       | Time complexity                                                        | Space complexity |
| --------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------- |
| Linear search ([details](Search/LinearSearch.md))               | O(N)                                                                   | O(1)             |
| Binary search ([details](Search/BinarySearch.md))               | O(log N)                                                               | O(1)             |
| Hashing ([details](Search/Hashing.md))                          | depends if all have the same hash it's O(N), O(1) if hashes are unique | O(N)             |


## Array operations

| Algorithm                                                                 | Time complexity | Space complexity |
| ------------------------------------------------------------------------- | --------------- | ---------------- |
| Swap ([details](ArrayOperations/Swap.md))                                 | O(1)            | O(1)             |
| Reverse ([details](ArrayOperations/Reverse.md))                           | O(N)            | O(1)             |
| Next Permutation ([details](ArrayOperations/NextPermutation.md))          | O(N)            | O(1)             |
| Quick select (nth Element) ([details](ArrayOperations/QuickSelect.md))    | O(N^2)          | O(1)             |
