# Deleting a node in Single Linked List

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

### Time complexity

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