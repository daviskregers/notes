# Zero/One knapsack problem


```
int knapsackAux(int[] profits, int[] weights, int capacity, int currentIndex)

    if capacity <= 0 || currentIndex < 0 || currentIndex >= profits.length
        return 0 // base case

    int profit1 = 0

    if (weights[currentIndex] <= capacity)
        
        profit1 = profits[currentIndex] + knapsackAux(profits, weights, capacity - weights[currentIndex], currentIndex + 1)

    int profit2 = knapsacAux(profits, weights, capacity, currentIndex + 1) // not taking the current element

    return Math.max(profit1, profit2)
```

## Top Down appoach

```
int knapsackAux(Integer[][] dp, int[] profits, int weights, int capacity, int currentIndex)

    if capacity <= 0 || currentIndex < 0 || currentIndex >= profits.length
        return 0

    if dp[currentIndex][capacity] != null
        return dp[currentIndex][capacity]

    int profit1 = 0

    if weights[currentIndex] <= capacity
        profit1 = profits[currentIndex] + knapsackAux(dp, profits, weights, capacity - weights[currentIndex], currentIndex + 1)

    int profit2 = knapsackAux(dp, profits, weights, capacity, currentIndex + 1)

    dp[currentIndex][capacity] = Math.max(profit1, profit2)

    return dp[currentIndex][capacity]
```

## Bottom Up approach

```
int solveKnapsack( int[] profits, int[] weights, int capacity)

    if capacity <= 0 || profits.length == 0 || weights.length != profits.length 
        return 0

    int[][] dp = new int[numberOfRows][capacity + 1]

    for int row = numberOfRows - 2; row >= 0; row --
        for int column = 1; column <= capacity; column++

            int profit1 = profit2 = 0

            if weights[row] <= column
                profit1 = profits[row] + dp[row + 1][column - weights[row]]

        profit2 = dp[row + 1][column]
        dp[row][column] = Math.max(profit1, profit2)

    return dp[0][capacity]

```