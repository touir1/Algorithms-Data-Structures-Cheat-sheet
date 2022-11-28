# Binary search cheat sheet (Java)

Conditions:

- Array must be sorted

The binary search algorithm is efficient for finding an element in a sorted array. It works by dividing at each iteration (repeatedly) in half the portion of the array that could contain the value. The algorithm stops when the portion is of size 1 (1 element remaining).

So, the algorithm goes as follows: (we're working with an array sorted in ascending order but we could also do it for decending order by inversing the checks)

1. Let left = 0 and right = n

2. let pivot as the half point between left and right (left + right / 2)

3. if pivot value = searched value, the algorithm stops (pivot contains the value)

4. if pivot value >  searched value the left pointer takes the value of pivot +1

5. if pivot value < searched value the right pointer takes the value of pivot - 1

6. if distance between left and right < 0, stop the algorithm, the value was not found

7. Else, go back to step 2

![](https://github.com/touir1/Algorithms-Data-Structures-Cheat-sheet/blob/main/Algorithms/Search/Images/Binary_search_animation.gif)

Here's the code for the binary search algorithm:

```java
int[] array = new int[] {1,3,11,23,42,54,59,67,70,73,75,80,81,83,87,92};

// we're looking for the element 59 in the array
int value = 59;
int found = -1;
// initializing left = 0 and right = size of array
int left = 0, right = array.length;
int pivot;

// continue while left <= right and value not found
while(left <= right) {
    pivot = (left+right)/2;

    if(array[pivot] == value) {
        found = pivot;
        break;
    }

    if(array[pivot] > value)
        right = pivot - 1;
    else
        left = pivot + 1;
}

// check if the element is found
if(found != -1)
    System.out.println("Element found at index: "+ found);
else
    System.out.println("Element was not found");
```

For the complexities:

- Time complexity: O(log N) as we're splitting the search by 2 at each iteration

- Space complexity: O(1) as we don't need extra space for the algorithm

Function implementation:

```java
public static int search(int[] array, int length, int element) {
    int left = 0, right = length - 1;
    int pivot;

    while(left <= right) {
        pivot = (left + right) / 2;

        if(array[pivot] == element) {
            return pivot;
        }

        if(array[pivot] > element)
            right = pivot - 1;
        else
            left = pivot + 1;
    }

    return -1;
}
```
