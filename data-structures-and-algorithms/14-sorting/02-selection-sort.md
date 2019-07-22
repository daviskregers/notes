# Selection sort

The selection sort algorithm is based on the idea of finding the minimum or maximum element in an unsorted array and then putting in it's correct position in a sorted array.

```
selectionSort(A)
    loop: j = 0 to n - 1
        int iMin = j
        loop: i = J + 1 to n - 1
            if(a[i] < a[iMin])
                iMin = i
        if(iMin != j)
            swap(a[j], a[iMin])

Time complexity - O(n^2)
Space complexity - O(1)
```

## When to use / avoid

- When to use:
    - When we don't have additional memory
    - Want easy implementation
- When to avoid
    - When time complexity is a concern