# Time and space complexity on array vs linked list

|                  | Time complexity (array) | Space complexity (array) | Time complexity (LL) | Space complexity (LL) |
|------------------|-------------------------|--------------------------|----------------------|-----------------------|
| create tree      | O(1)                    | O(n)                     | O(1)                 | O(1)                  |
| insert           | O(1)                    | O(1)                     | O(n)                 | O(n)                  |
| delete           | O(n)                    | O(1)                     | O(n)                 | O(n)                  |
| search           | O(n)                    | O(1)                     | O(n)                 | O(n)                  |
| traverse         | O(n)                    | O(1)                     | O(n)                 | O(n)                  |
| delete           | O(1)                    | O(1)                     | O(1)                 | O(1)                  |
| space efficient? |                         | NO                       |                      | YES      |

In this case where neither of the implementations are better. Using arrays is faster, but it has a limited size. Where LinkedLists are more space efficient but is slower.

