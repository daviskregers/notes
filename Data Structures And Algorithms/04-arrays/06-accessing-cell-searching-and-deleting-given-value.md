# Accessing cell, searching and deleting given value

## Accessing given cell of 1D array

```
AccessingCell(arr, cellNumber):
    if (cellNumber > sizeof(arr))
        return exception // cell number cannot be bigger than size of array
    else
        return arr[cellNumber]

Total time complexity  = O(1)
Total space complexity = O(1)
```

## Searching a given value in 1D array

We can search the given array for a value and return it's index if it's found.

```
SearchInArray(arr, valueToSearch):
    loop: i = 0 to arr.length
        if( arr[i] equals valueToSearch )
            return i
    return error // value not found

Total time complexity - O(n)
Space complexity - O(1)
```



## Deleting a given value from 1D array

Practically speaking, we can never delete a value from an array, but you can assign a value that can be assumed as a blank value like `0` or other value that will not be used.

```
DeletingValueFromArray(arr, location):
    if(arr[location] is occupied)
        arr[location] = Integer.MinValue 
    else
        return // location is already blank

Total time complexity  = O(1)
Total space complexity = O(1)
```

