# Insert and traverse in 1d array

## Inserting a value in 1D array

To insert a value in a cell, all we have to do is to point at the cell and tell it's value.

```java
arr[4] = 50;
arr[5] = 60;
```

We can write a function for it:

```
insert (arr, valueToBeInserted, location):
    if(arr[location] is ocupied)
        return error // location is already occupied
    ... additional validation
    else
        arr[location] = valueToBeInserted

```

Time complexity

```
insert (arr, valueToBeInserted, location):
    if(arr[location] is ocupied) ------------------------ O(1) ----|
        return error // location is already occupied ---- O(1) ----|
    ... additional validation -------------------------------------|- O(1)
    else ------------------------------------------------ O(1) ----|
        arr[location] = valueToBeInserted --------------- O(1) ----|


Total time complexity - O(1)
Space complexity - O(1)

```

## Traversing a given 1D array

By traversing it is meant to visit each and every cell of the array for printing or other purpose. 

We can write a function that does that by doing following:

```
TraverseArray(arr):
    loop: i = 0 to arr.length
        print arr[i]
```

Time complexity:

```
TraverseArray(arr):
    loop: i = 0 to arr.length ------ O(n)
        print arr[i] --------------- O(1)

Total time complexity - O(n)
Space complexity      - O(1)
```
