# Linear queue implementation with LinkedList

```
createQueue()
    create a blank SingleLinkedList

Time Complexity - O(1)
Space Complexity - O(1)
```

```
enqueue(nodeValue):
    create a node
    node.value = nodeValue
    node.next = null
    if tail == null // queue empty
        tail = node
    else 
        tail.next = node
        tail = node

Time Complexity - O(1)
Space Complexity - O(1)
```

```
deQueue()
    if head == null
        return error
    tmpNode = head
    head = head.next
    return tmpNode.value

Time Complexity - O(1)
Space Complexity - O(1)
```

```
peek()
    if head == null
        return error
    return head.value

Time Complexity - O(1)
Space Complexity - O(1)
```

```
isQueueEmpty()
    if head == null
        return true
    return false

Time Complexity - O(1)
Space Complexity - O(1)
```

```
deleteQueue()
    head = tail = null

Time Complexity - O(1)
Space Complexity - O(1)
```

## Time and space complexity of lineart queue

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create queue | O(1)            | O(n)             |
| enqueue      | O(1)            | O(1)             |
| dequeue      | O(1)            | O(1)             |
| peek         | O(1)            | O(1)             |
| isEmpty      | O(1)            | O(1)             |
| isFull       | N/A             | N/A              |
| delete queue | O(1)            | O(1)             |

Again, isFull is not implemented because linked list can dinamically change it's size.