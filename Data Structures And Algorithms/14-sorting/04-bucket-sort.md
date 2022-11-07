# Bucket sort

Bucket sort is a sorting algorithm that works by:
1. distributing the elements of an array into a number of buckets.

    ```
    Create number of buckets = ceil/floor(sqrt(total number of items))

    iterate through each number and place it in approriate bucket

    Approriate bucket = ceil((value * number of buckets) / max value in array)

    ```

2. Sort all buckets
3. Merge all the buckets

```
BucketSort(A)
    find no of buckets to be created and create those buckets
    find divisor value
    loop: i = 0 to n-1
        insert A[i] into array B[] using divisor and bucket#
    sort B[] with insertion sort (or any sort)
    concatenate B1[], B2[], B3[]...

Time Complexity - O(n log n)
Space Complexity - O(n)
```

## When to use

- When input is uniformly distributed over a range
- Biggest advantage of bucket sort (compared to other sorting algorithms) is that each bucket can be sorted independently, which makes it great for distributed computing.

## When to avoid
- When space is a concern