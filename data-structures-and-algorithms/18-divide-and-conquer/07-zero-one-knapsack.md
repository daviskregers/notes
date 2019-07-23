# Zero/One knapsack

Given the weights and profits of N items. We are asked to put these items in a knapsack which has capacity C. Restriction is, that we cannot break the item into smaller units. Challenge is to find the maximum profit from the items in the knapsack.

Example:

    Items: {Mango, Apple, Banana, Orange}
    Profits: {31, 26, 72, 17}
    Weights: {3, 1, 5, 2}
    Knapsack capacity: 7

    Now we will try to find max profit by collection different combinations of fruits in the knapsack, such that their total weight is not more than 7:

    Mango + Apply + Orange (total weight 6) => 74
    Orange + Banana (total weight 7) => 89
    Apple + Banana (total weight 6) => 98

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