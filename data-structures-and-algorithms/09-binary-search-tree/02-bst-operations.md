# Binary search tree operations

```
createBST()
    initialize root with null

Time complexity  - O(1)
Space complexity - O(1)
```

```
searchBST(root, value): ----------------- T(n)
    if root == null --------------------- O(1)
        return null --------------------- O(1)
    else if root == value --------------- O(1)
        return root --------------------- O(1)
    else if value < root ---------------- O(1)
        searchBST(root.left, value) ----- T(n/2)
    else if value > root ---------------- O(1)
        searchBST(root.right, value) ---- T(n/2)

Time complexity  - O(log n)
Space complexity - O(log n)
```

```
preOrderTraversal(root) ----------------- T(n)
    if root == null --------------------- O(1)
        return error -------------------- O(1)
    print root -------------------------- O(1)
    preOrderTraversal(root.left) -------- T(n/2)
    preOrderTraversal(root.right) ------- T(n/2)

Time complexity  - O(n)
Space complexity - O(n)
```

```
inOrderTraversal(root) ----------------- T(n)
    if root == null --------------------- O(1)
        return error -------------------- O(1)
    inOrderTraversal(root.left) -------- T(n/2)
    print root -------------------------- O(1)
    inOrderTraversal(root.right) ------- T(n/2)

Time complexity  - O(n)
Space complexity - O(n)
```

```
postOrderTraversal(root) ----------------- T(n)
    if root == null --------------------- O(1)
        return error -------------------- O(1)
    postOrderTraversal(root.left) -------- T(n/2)
    postOrderTraversal(root.right) ------- T(n/2)
    print root -------------------------- O(1)

Time complexity  - O(n)
Space complexity - O(n)
```

```
levelOrderTraversal(root)
    create a queue(Q)
    enqueue(root)
    while(queue not empty)
        dequeue() and print
        enqueue the child of dequeued element

Time complexity  - O(n)
Space complexity - O(n)
```

```
insertBST(currentNode, valueToInsert)
    if currentNode == null
        create a node, insert valueToInsert in it
    else if (valueToInsert <= currentNode.value)
        currentNode.left = insertBST(currentNode.left, valueToInsert)
    else currentNode.right = insertBST(currentNode.right, valueToInsert)

    return currentNode

Time complexity  - O(log n)
Space complexity - O(log n)
```
    
```
deleteBST(root, valueToBeDeleted)
    if root == null 
        return null

    if valueToBeDeleted < root.value
        root.left = deleteBST(root.left, valueToBeDeleted)
    else if valueToBeDeleted > root.value
        root.right = deleteBST(root.right, valueToBeDeleted)
    else // if current node is the node to be deleted
        if root have both children, then find minimum element from right subtree
            replace current node with minimum node from right subtree and delete minimum node from right
        else if nodeToBeDeleted has only right child
            root = root.right
        else // if nodeToBeDeleted does not have children
            root = null

    return root

Time complexity  - O(log n)
Space complexity - O(log n)
```

```
deleteBST()
    root = null

Time complexity  - O(1)
Space complexity - O(1)
```


## Time and space complexity

|              | Time complexity | Space complexity |
|--------------|-----------------|------------------|
| create tree | O(1)            | O(1)             |
| insert value      | O(log n)            | O(log n)             |
| delete value      | O(n)            | O(n)             |
| search         | O(log n)            | O(log n)             |
| traverse      | O(log n)            | O(log n)             |
| delete tree       | O(1)            | O(1)             |