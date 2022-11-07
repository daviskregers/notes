# Single linked list

![](../../images/2019-06-12-18-51-06.png)

## Creating

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

## Inserting

We can assume that we have a Single Linked List with 6 elements in it.

![](../../images/2019-06-12-18-51-06.png)

When we want to insert a new node, we can have 3 scenarios:
- Inserting at the start of linked list

    We have to create a new node, hold a reference to the first element and update the head to reference it.

- Inserting at the end of linked list

    We have to create a new node, update the previous element as well as the tail to point to it.

- Inserting at a specified location in linked list

    We have to create a new node, update the previous element to point to it, hold the reference to the next element.


```
insertInLinkedList(head, nodeValue, location)
    create a blank node
    node.value = nodeValue
    if( !existsLinkedList(head) )
        return error // LinkedList does not exist
    else if (location equals 0) // insert at first position
        node.next = head
        head = node
    else if (location equals last) // insert at last position
        node.next = null
        last.next = node
        last = node // to keep track of the last node
    else 
        loop: tmpNode = 0 to location - 1
        node.next = tmpNode.next
        tmpNode.next = node
```

```
insertInLinkedList(head, nodeValue, location)
    create a blank node ------------------------------------------- O(1)
    node.value = nodeValue ---------------------------------------- O(1)
    if( !existsLinkedList(head) ) --------------------------------- O(1)
        return error // LinkedList does not exist ----------------- O(1)
    else if (location equals 0) // insert at first position ------- O(1)
        node.next = head ------------------------------------------ O(1)
        head = node ----------------------------------------------- O(1)
    else if (location equals last) // insert at last position ----- O(1)
        node.next = null ------------------------------------------ O(1)
        last.next = node ------------------------------------------ O(1)
        last = node // to keep track of the last node ------------- O(1)
    else  --------------------------------------------------------- O(1)
        loop: tmpNode = 0 to location - 1 ------------------------- O(n)
        node.next = tmpNode.next ---------------------------------- O(1)
        tmpNode.next = node --------------------------------------- O(1)

Time complexity  O(n)
Space complexity O(1)
```

## Traversal 

```
TraverseLinkedList(head):
    if head == null return;
    loop: head to tail
        print currentNode.value
```

```
TraverseLinkedList(head):
    if head == null return; -------------- O(1)
    loop: head to tail ------------------- O(n)
        print currentNode.value ---------- O(1)

Time complexity - O(n)
Space complexity - O(1)
```

## Search

```
SearchNode(head, nodeValue):
    loop: tmpNode = start to tail
        if( tmpNode.value equals nodeValue )
            print tmpNode.value // node value found
            return
    return // nodeValue node found
```

```
SearchNode(head, nodeValue):
    loop: tmpNode = start to tail ------------------------- O(n)
        if( tmpNode.value equals nodeValue ) ---------|
            print tmpNode.value // node value found --|- O(1)
            return -----------------------------------|
    return // nodeValue node found ------------------------ O(1)

Time complexity  O(n)
Space complexity O(1)
```

## Deleting a node

There can be 3 cases:
- Delete first element

    Delete node, update head to point to second element.

- Delete last element

    Delete node, update tail to point to previous element.

- Delete a specified node

    Delete node, update previous element to point to next.

```
DeleteNode(head, location):
    if(!existsLinkedList(head))
        return error // linked list does not exist
    else if (location equals 0) // delete first node
        head = head.next
        if this is the only element in the list, update tail = null
    else if (location >= last)
        if current node is only node in list
            head = tail = null return;
        else 
            loop till 2nd last node (tmpNode)
        tail = nmpNode; tmpNode.next = null;
    else
        loop: tnpNode = start to location - 1
        tmpNode.next = tmpNode.next
```

```
DeleteNode(head, location):
    if(!existsLinkedList(head)) --------------------------------------- O(1)
        return error // linked list does not exist -------------------- O(1)
    else if (location equals 0) // delete first node ------------------ O(1)
        head = head.next ---------------------------------------------- O(1)
        if this is the only element in the list, update tail = null --- O(1)
    else if (location >= last) ---------------------------------------- O(1)
        if current node is only node in list -------------------------- O(1)
            head = tail = null return; -------------------------------- O(1)
        else  --------------------------------------------------------- O(1)
            loop till 2nd last node (tmpNode) ------------------------- O(n)
        tail = nmpNode; tmpNode.next = null; -------------------------- O(1)
    else -------------------------------------------------------------- O(1)
        loop: tnpNode = start to location - 1 ------------------------- O(n)
        tmpNode.next = tmpNode.next ----------------------------------- O(1)

Time complexity  O(n)
Space complexity O(1)
```

## Delete entire Single Linked List

```
DeleteLinkedList(head, tail):
    head = null
    tail = null
```

```
Time complexity  O(1)
Space complexity O(1)
``

## Time complexity

|                     | Time complexity | Space complexity |
|---------------------|-----------------|------------------|
| Creating            | O(1)            | O(1)             |
| Insertion           | O(n)            | O(1)             |
| Searching           | O(n)            | O(1)             |
| Traversing          | O(n)            | O(1)             |
| Deletion            | O(n)            | O(1)             |
| Deleting whole list | O(1)            | O(1)             |