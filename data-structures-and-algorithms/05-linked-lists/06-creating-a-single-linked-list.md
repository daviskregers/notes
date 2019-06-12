# Creating a single linked list

When we want to create a single linked list, it consists of a few steps:
1. We create a blank head reference
2. We create a blank tail reference
3. We initialize them both with null
4. We create a blank node
5. We initialize it with null reference
6. We initialize the data part of it
7. We update the head reference to the node
8. We update the tail reference to the node

```
createSingleLinkedList(node):
    create a head, tail pointer and initialize with NULL
    create a blank node
    node.value = nodeValue
    head = node
    tail = node
```

## Time complexity

```
createSingleLinkedList(node):
    create a head, tail pointer and initialize with NULL ---- O(1)
    create a blank node ------------------------------------- O(1)
    node.value = nodeValue ---------------------------------- O(1)
    head = node --------------------------------------------- O(1)
    tail = node --------------------------------------------- O(1)

Time complexity  O(1)
Space complexity O(1)
```

