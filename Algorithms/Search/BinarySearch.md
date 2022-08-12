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

6. if distance between left and right < = 1, stop the algorithm, the value was not found

7. Else, go back to step 2
