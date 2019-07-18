# AVL implementation

```
createAVL()
    root = null

Time complexity  - O(1)
Space complexity - O(1)
```

```
searchAVL(root, value)
    if( root is null )
        return null
    else if root == value
        return root
    else if value < root
        searchAVL(root.left, value)
    else if value > root
        searchAVL(root.right, value)

Time complexity  - O(log n)
Space complexity - O(log n)
```

```
preOrderTraversal(root)
    if root == null
        return error
    
    print root
    preOrderTraversal(root.left)
    preOrderTraversal(root.right)

Time complexity  - O(n)
Space complexity - O(n)
```

```
inOrderTraversal(root)
    if root == null
        return error
    
    inOrderTraversal(root.left)
    print root
    inOrderTraversal(root.right)
    
Time complexity  - O(n)
Space complexity - O(n)
```

```
postOrderTraversal(root)
    if root == null
        return error
    
    postOrderTraversal(root.left)
    postOrderTraversal(root.right)
    print root

Time complexity  - O(n)
Space complexity - O(n)
```

```
levelOrderTraversal(root)
    create a queue
    enqueue(root)
    while(queue not empty)
        dequeue and print
        enqueue children

Time complexity  - O(n)
Space complexity - O(n)   
```

Insertion:
- Case 1 - rotation not required
- Case 2 - rotation required (LL, LR, RR, RL)

