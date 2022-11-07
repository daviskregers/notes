# Circular double linked list

![](../../images/2019-06-12-19-09-10.png)

A linked list that is similar to circular single linked list, but it has 2 references - to previous and next nodes.

## Creating

```
createCircularDoubleLinkedList(nodeValue):
    create a blank node
    node.value = nodeValue
    head = node
    tail = node
    node.next = node.prev = node

Time complexity - O(1)
Space complexity - O(1)
```

## Insert

```
insert(head, nodeValue, location):
    create a blank node
    node.value = nodeValue

    if(!existsLinkedList(head))
        return error
    else if (locations == 0)
        node.next = head
        node.prev = tail
        head.prev = node
        head = node;
        tail.next = node
    else if (location == last)
        node.next = head; node.prev = last;
        head.prev = node
        last.next = node
        tail = node
    else // at specific location
        loop: tmpNode = 0 to location -1
            node.next = tmpNode.next; node.prev = tmpNode
            tmpNode.next = node; node.next.prev = node

Time complexity - O(n)
Space comlexity - O(1)
```

## Traverse

```
traverse():
    if head == null
        return
    
    loop: head to tail
        print currentNode.value

Time complexity - O(n)
Space complexity - O(1)
```

## Search

```
searchNode(nodeValue):
    loop: tmpNode = head to tail
        if(tmpNode.value == nodeValue)
            print tmpNode.value
            return true
    return false

Time complexity - O(n)
Space complexity - O(1)
```

## Delete

```
delete(head, location):

    if(!existsLinkedList(head))
        return error
    else if (location == 0)
        if(only one element)
            head.next = head.prev = head = tail = null;
            return
        head = head.next
        head.prev = null
        tail.next = head
    else if (location >= last)
        if(only one element)
            head.next = head.prev = head = tail = null;
            return
        tail = tail.prev; tail.next = head; head.prev = tail
    else 
        loop: tmpNode = head to location -1 
        tmpNode.next = tmpNode.next.next
        tmpNode.next.prev = tmpNode

Time complexity - O(n)
Space complexity - O(1)

```

## Delete entire CDLL

```
deleteLinkedList(head, tail):
    tail.next = null
    loop(tmp:head to tail)
        tmp.prev = null
    head = tail = null

Time complexity - O(n)
Space complexity - O(1)
```

## Time and space complexityies

|                     | Time complexity | Space complexity |
|---------------------|-----------------|------------------|
| Creating            | O(1)            | O(1)             |
| Insertion           | O(n)            | O(1)             |
| Searching           | O(n)            | O(1)             |
| Traversing          | O(n)            | O(1)             |
| Deletion            | O(n)            | O(1)             |
| Deleting whole list | O(n)            | O(1)             |