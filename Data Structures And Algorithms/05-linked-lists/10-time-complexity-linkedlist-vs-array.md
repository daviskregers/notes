# Time complexity (linked list vs array)

|                                  | Array    | LinkedList  |
|----------------------------------|----------|-------------|
| Create                           | O(1)     | O(1)        |
| Insertion at 1st position        | O(1)     | O(1)        |
| Insertion at last position       | O(1)     | O(1)        |
| Insertion at n-th position       | O(1)     | O(n)        |
| Deletion from 1st position       | O(1)     | O(1)        |
| Deletion from last position      | O(1)     | O(n) / O(1) |
| Deletion from n-th position      | O(1)     | O(n)        |
| Searhing in unsorted data        | O(n)     | O(n)        |
| Searching in sorted data         | O(log n) | O(n)        |
| Accessing n-th element           | O(1)     | O(n)        |
| Traversing                       | O(n)     | O(n)        |
| Deleting entire Array/LinkedList | O(1)     | O(n) / O(1) |