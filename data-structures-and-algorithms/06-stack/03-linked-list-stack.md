# Linked list stack

```
createStack()
    create an object of SingleLinkedList class

Time complexity - O(1)
Space complexity - O(1)
```

```
push(nodeValue) // insert an element between head and first element
    create a node
    node.value = nodeValue
    node.next = head
    head = node

Time complexity - O(1)
Space complexity - O(1)
```

```
pop(): // return and remove the element head points to
    if isEmpty()
        return error
    
    tmpNode = head
    head = head.next
    return tmpNode.value

Time complexity - O(1)
Space complexity - O(1)
```

```
peek()
    return head.value

Time complexity - O(1)
Space complexity - O(1)
```

```
isEmpty()
    if head == null
        return true
    return false

Time complexity - O(1)
Space complexity - O(1)
```

```
deleteStack()
    head = null

Time complexity - O(1)
Space complexity - O(1)
```

## Time and space complexity

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create stack | O(1)            | O(n)             |
| push         | O(1)            | O(1)             |
| pop          | O(1)            | O(1)             |
| peek         | O(1)            | O(1)             |
| isEmpty      | O(1)            | O(1)             |
| isFull       | N/A             | N/A             |
| delete stack | O(1)            | O(1)             |

Note that the `isFull` method is not implemented, since the linked list can have as many elements as we want, provided our memory can hold it.

Apart from that, the only difference is that when using linked list,
the stack creation method uses space complexity of O(1) instead of O(n) since we create only one node not reserve the whole array.


