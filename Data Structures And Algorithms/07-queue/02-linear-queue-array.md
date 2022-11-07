# Linear queue on array

```
createQueue(size)
    create a blank array of `size`
    initialize topOfQueue, beginingOfQueue to -1

Time complexity O(1)
Space complexity O(n)
```

```
enQueue(value)
    if queue is full
        return error
    arr[topOfQueue + 1] = value
    topOfQueue++

Time complexity O(1)
Space complexity O(1)
```

```
deQueue()
    if queue is empty
        return error
    print arr[beginningOfQueue]
    beginningOfQueue++
    if( beginningOfQueue > endOfQueue ) // all elements dequeued
        beginningOfQueue = topOfQueue = -1

Time complexity - O(1)
Space complexity - O(1)
```

```
peek()
    if queue empty
        return error
    print arr[beginningOfQueue]

Time complexity - O(1)
Space complexity - O(1)
```

```
isQueueEmpty()
    return beginningOfQueue == -1

Time complexity - O(1)
Space complexity - O(1)
```

```
isQueueFull()
    return (beginningOfQueue == arr.length - 1)

Time complexity - O(1)
Space complexity - O(1)
```

```
deleteQueue()
    array = null
```

## Time and space complexity of lineart queue

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create queue | O(1)            | O(n)             |
| enqueue      | O(1)            | O(1)             |
| dequeue      | O(1)            | O(1)             |
| peek         | O(1)            | O(1)             |
| isEmpty      | O(1)            | O(1)             |
| isFull       | O(1)            | O(1)             |
| delete queue | O(1)            | O(1)             |