# Time and Space complexity on array vs linked list

|                  | Time complexity (array) | Space complexity (array) | Time complexity (LL) | Space complexity (LL) |
|------------------|-------------------------|--------------------------|----------------------|-----------------------|
| create queue     | O(1)                    | O(n)                     | O(1)                 | O(1)                  |
| enqueue          | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| dequeue          | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| peek             | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| isEmpty          | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| isFull           | O(1)                    | O(1)                     | N/A                  | N/A                   |
| delete queue     | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| Space efficient? |                         | NO                       |                      | YES                   |

When we compare both implementations of arrays and linked lists, we can say that both implementations are relatively the same, but the linked lists are more space efficient.