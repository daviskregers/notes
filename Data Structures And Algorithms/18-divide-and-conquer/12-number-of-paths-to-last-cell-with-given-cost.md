# Number of paths to last cell with given cost

We are given a 2D matrix. Accessing each cell has a cost associated to it. We need to start from (0,0) and go to (n-1, n-1) cell. We are given total cost to reach the end of the array. We can go only right or down cell from current cell. Challenge is to find the number of ways to reach end of matrix given the total cost.

```
int numberOfPaths(int array[][], int row, int cost)
    if(cost < 0)
        return 0
    if row == 0 && col == 0
        return array[0][0] - cost == 0 ? 1 : 0
    if row == 0 // at first row, we can only go left
        return NumberOfPaths(array, 0, col - 1, cost - array[row][col])
    if col == 0
        return NumberOfPaths(array, row - 1, 0, cost - array[row][col])

    int noOfPathsFromPreviousRow = numberOfPaths(array, row - 1, col, cost - array[row][col])
    int noOfPathsFromPreviousCol = numberOfPaths(array, row, col - 1, cost - array[row][col])

    return noOfPathsFromPreviousRow + noOfPathsFromPreviousCol
```