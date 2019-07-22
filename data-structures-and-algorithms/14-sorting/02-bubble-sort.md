# Bubble sort

- This is the simples of all the sorting algorithms.
- Sometimes referred as sinking sort
- Repeadly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order.

```
bubbleSort(int arr[])
    int n = arr.length
    for(int i = 0; i < n -1; i++) // run from first cell to last cell
        for( int j = 0; j < n - i - 1; j++ ) // run from first cell to last cell - iteration
            if(arr[j] > arr[j + 1])
                swap(arr[j], arr[j+1])

Time complexity O(n^2)
Space complexity O(1)
```

## When to use/avoid bubble sort:

- When to use:
    - When input is already sorted
    - Space is a concern
    - Easy to implement
- When to avoid
    - Average case time complexity is poor