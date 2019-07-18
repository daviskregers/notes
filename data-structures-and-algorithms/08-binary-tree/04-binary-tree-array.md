# Binary tree with array

```
createBinaryTree(size)
    create a blank array of `size`
    update lastUsedIndex to 0

Time complexity - O(1)
Space complexity - O(n)
```

```
insertValueInBinaryTree()
    if Tree is full
        return error
    else
        insert value in first unused cell of array
        update lastUsedIndex

Time complexity - O(1)
Space complexity - O(1)  
```

```
searchValueInBinaryTree()
    traverse the entire array from 1 to lastUsedIndex
    if value found
        return true
    return false

Time complexity - O(n)
Space complexity - O(1)   
```

```
inOrderTraversal(index)
    if index > lastUsedIndex
        return
    
    inOrderTraversal(index * 2)
    print current_index.value
    inOrderTraversal(index * 2 + 1)

Time complexity - O(n)
Space complexity - O(n) --- each recursion call is pushed to stack
```

```
preOrderTraversal(index)
    if index > lastUsedIndex
        return
    print current_index.value
    preOrderTraversal(index * 2)
    preOrderTraversal(index * 2 + 1)

Time complexity - O(n)
Space complexity - O(n) --- each recursion call is pushed to stack
```

```
postOrderTraversal(index)
    if index > lastUsedIndex
        return
    
    postOrderTraversal(index * 2)
    postOrderTraversal(index * 2 + 1)
    print current_index.value

Time complexity - O(n)
Space complexity - O(n) --- each recursion call is pushed to stack
```

```
levelOrderTraversal()
    loop 1 to lastUsedIndex
        print current_index.value

Time complexity - O(n)
Space complexity - O(1)
```

```
deleteNodeFromBinaryTree()
    search for desired value in array ------- O(n)
        if value found
            replace cell with last cell and update lastUpdatedIndex
    return error

Time complexity - O(n)
Space complexity - O(1)
```

```
deleteBinaryTree()
    set array as null


Time complexity - O(1)
Space complexity - O(1)
```

## Time and space complexity

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create tree | O(1)            | O(n)             |
| insert value      | O(1)            | O(1)             |
| delete value      | O(n)            | O(1)             |
| search         | O(n)            | O(1)             |
| traverse      | O(n)            | O(1)             |
| delete tree       | O(1)            | O(1)             |