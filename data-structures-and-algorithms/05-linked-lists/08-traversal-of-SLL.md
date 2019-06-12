# Traversal of Single Linked List

```
TraverseLinkedList(head):
    if head == null return;
    loop: head to tail
        print currentNode.value
```

### Time complexity

```
TraverseLinkedList(head):
    if head == null return; -------------- O(1)
    loop: head to tail ------------------- O(n)
        print currentNode.value ---------- O(1)
```