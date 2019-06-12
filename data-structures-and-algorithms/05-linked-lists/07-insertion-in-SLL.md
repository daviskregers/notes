# Insertion in Single Linked List

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

### Time complexity

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