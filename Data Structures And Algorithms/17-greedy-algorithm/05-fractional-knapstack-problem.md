# Fractional Knapstack Problem

Fill the knapstack such that the value is maximum and total weight is atmost W. Items can be broken down to maximize knapsack value.

## Assumtions
- Every type of itam has only 1 qty available
- Items can be broken down into fractions

## Example

So we have 3 types of items:
- value: $100, weight: 20kg (A)
- value: $120, weight: 30kg (B)
- value: $60, weight: 10kg (C)

Max knapsack capacity is 50kg.

So, we take C, A and 2/3 of B
Total weight - 10 + 20 + 30*2/3 = 50
Total value - 60+100+120*2/3 = 240

## Algorithm

1. Calculate the ration (value/weight) for each item
2. Sort the items based on this ration
3. Take the items with the highes ration sequentially as long as the weight allows
4. At the end add the next item as much (fractional) as we can

```
FractionalKnapsackProblem(CapactityOfKnsapsack, A[][])
    initialize ratio[]
    ratio = CalculateRatio(A)
    SortDescending(ratio[])
    loop: i = 0 to n - 1
        if( totalWeight + currentItemWeight < knapsackCapacity )
            consume (A[i][0])
            totalWeight = totalWeight + currentItemWeight
        else
            consumeFraction(A[i][0]); break;

Time complexity - O(n log n)
Space complexity - O(n)
```
