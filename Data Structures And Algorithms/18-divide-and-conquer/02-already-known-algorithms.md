# Already known algorithms

## Binary Search

```
BinarySearch(int findNumber, int arr[], start, end)
    mid = FindMid(arr[], start, end)
    if mid > findNumber
        BinarySearch(int findNumber, int arr[], start, mid)
    else if mid < findNumber
        BinarySearch(int findNumber, int arr[], mid, end)
    else if mid == findNumber
        return mid
```

## Merge Sort algorithm

```
mergeSort(A, l, r)
    if r > l
        middle m = (l+r)/2
        mergeSort(A,l,m)
        mergeSort(A,m+1,r)
        merge(A,I,m,r)

merge(A,p,m,r)
    create tmp arrays L & R and copy A,p,m into L & A,m+1,r into R
    i = j = 0
    loop: k = p to r
        if L[i] < R[j]
            A[k] = L[i]; i++
        else
            A[k] = R[j]; j++
```

## Quick Sort

```
QuickSort(A, p, q)
    if(p < q)
        r = partition(A,p,q)
        QuickSort(A,p,r-1)
        QuickSort(A,r+1,p)

partition(A,p, q)
    pivot = q
    i = p - 1
    for(j = p to q)
        if A[i] <= A[pivot]
            increment i and swap(A[i], [j])
```