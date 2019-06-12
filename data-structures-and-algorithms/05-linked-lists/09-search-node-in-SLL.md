# Search node in Single Linked List

```
SearchNode(head, nodeValue):
    loop: tmpNode = start to tail
        if( tmpNode.value equals nodeValue )
            print tmpNode.value // node value found
            return
    return // nodeValue node found
```

### Time complexity

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

