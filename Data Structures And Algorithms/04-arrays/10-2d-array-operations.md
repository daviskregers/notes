# 2D array operations

## Inserting a value in 2D array

```
Insert(arr, valueToBeInserted, rowNumber, colNumber):
    if(arr[rowNumber][colNumber] is occupied)
        return error // already ocupied
    else
        arr[rowNumber][colNumber] = valueToBeInserted
```

### Time complexity

```
Insert(arr, valueToBeInserted, rowNumber, colNumber):
    if(arr[rowNumber][colNumber] is occupied) ---------- O(1)
        return error // already ocupied ---------------- O(1)
    else ----------------------------------------------- O(1)
        arr[rowNumber][colNumber] = valueToBeInserted -- O(1)


Time complexity  O(1)
Space complexity O(1)
```

## Traversing

```
TraverseArray(arr):
    loop: row = 0 to rows
        loop: col = 0 to rows
            print arr[row][col]
```

### Time complexity

```
TraverseArray(arr):
    loop: row = 0 to rows ----------- O(m)
        loop: col = 0 to rows ------- O(n)
            print arr[row][col] ----- O(1)

Time complexity  O(mn)
Space complexity O(1)
```

## Searching a given value in 2D array

```
SearchInArray(arr, valueToSearch):
    loop: row = 0 to rows
        loop: col = 0 to cols
            if( arr[row][col]] equals valueToSearch )
                print(row,col); return;
    print (value not found)
```

### Time complexity

```
SearchInArray(arr, valueToSearch):
    loop: row = 0 to rows --------------------------------- O(m)
        loop: col = 0 to cols ----------------------------- O(n)
            if( arr[row][col]] equals valueToSearch ) ----- O(1)
                print(row,col); return; ------------------- O(1)
    print (value not found) ------------------------------- O(1)

Time complexity  O(mn)
Space complexity O(1)
```

## Deleting a given value

```
DeletingValue(arr, rowNumber, colNumber):
    arr[rowNumber][colNumber] = Integer.MIN_VALUE;
```

### Time complexity

```
DeletingValue(arr, rowNumber, colNumber):
    arr[rowNumber][colNumber] = Integer.MIN_VALUE; ---------------- O(1)

Time complexity  O(1)
Space complexity O(1)
```