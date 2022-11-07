# Heap Sort

Heap Sort works by first organizing the data to be sorted into a spacial type of binary tree called heap.

Then it removes the topmost item (the larges/smallest) and inserts into current array. It keeps until Binary Heap is not empty.

Is best suited with arrays. Does not work best with Linked Lists.

```
HeapSort(A)
    for i = 0 to A.length -1
        insertInHeap(A[i])
    for i = 0 to A.length -1
        extractFromHeap(A[i])

Time complexity - O(n logn)
Space complexity - O(1)
```

## When to use
- When space is a concern

## When to avoid
- When we need our sort to be stable

