# Stack structure using arrays

When using an array to build a stack, the advantage is that it is easy to implement, but however, the stack can only be fixed size.

```
createStack(int size):
    create blank array of `size`
    initialize variable topOfStack to -1

Time complexity - O(1)
Space complexity - O(n)
```

```
push(value):
    if stack is full
        return error 
    else 
        insert value at the top of the array
        topofStack++


Time complexity - O(1)
Space complexity - O(1)
```

```
pop()
    if stackIsEmpty()
        return error
    else
        print top of stack
        topOfStack--

Time complexity - O(1)
Space complexity - O(1)      
```

```
peek()
    if stackIsEmpty()
        return error
    else
        print topOfStack

Time complexity - O(1)
Space complexity - O(1)  
```

```
isEmpty():
    if (topOfStack == -1)
        return true
    return false

Time complexity - O(1)
Space complexity - O(1)  
```

```
isFull():
    if(topOfStack === arr.size)
        return true
    return false

Time complexity - O(1)
Space complexity - O(1)  
```

```
deleteStack()
    arr = null

Time complexity - O(1)
Space complexity - O(1)  
```

## Time and space complexity when using array

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create stack | O(1)            | O(n)             |
| push         | O(1)            | O(1)             |
| pop          | O(1)            | O(1)             |
| peek         | O(1)            | O(1)             |
| isEmpty      | O(1)            | O(1)             |
| isFull       | O(1)            | O(1)             |
| delete stack | O(1)            | O(1)             |