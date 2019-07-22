# Insertion sort

In insertion sort algorithm we:
1. Divide the given array into 2 parts - sorted and unsorted.
2. Then from unsorted array we pick the first element and find it's correct position in sorted array.
3. Repeat while unsorted array is not empty

```
insertionSort(A)
    loop: i = 1 to n
        currentNumber = A[i], j=i
        while(A[j-1] > currentNumber && j > 0)
            J[j] = A[j-1]
            j--
        A[j] = currentNumber

Time complexity - O(n^2)
Space complexity - O(1)
```

## When to use / avoid

- When to use
    - No extra space
    - Simple implementation
    - Best when we have continuous inflow of numbers and we want to keep the list sorted.
- When not to use
    - Average time complexity is bad

