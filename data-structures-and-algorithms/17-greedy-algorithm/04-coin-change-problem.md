# Coin change problem

Given a value V, we want to make changes for V dollars. We have infinite supply of each of the denominations in US currency. i.e. we have infinite supply of {1,2,5,10,20,50,100,500,1000} valued coins/notes, which is the miniumum number of coins and/or notes needed to make the changes for $V?

## Example

Input value V=70
Output = 2
Breakdown - $50 * 1 + $20 * 1

## Example 2

Input value V=121
Output - 3
Breakdown - $100 * 1 + $20 * 1 + $1 * 1

## Solution

1. Initialize results as empty
2. Find the largest denomination that is smaller than V
3. Add found denomination to result. 
4. Substract value of found denomination from V.
5. If V becomes 0, then print result.
6. Else go to step 2

```
CoinChangeProblem(N)
    initialize result as empty
    loop: until it self breaks
        MaxDenomination = FindLargestDenominationLesserThan(N)
        Insert(result, MaxDenomination)
        N = N - MaxDenomination
        if N == 0
            print result and exit

Time Complexity - O(n)
Space Complexity - O(V) (length of the array to return)
```



