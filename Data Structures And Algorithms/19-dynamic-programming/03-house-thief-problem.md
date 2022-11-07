# House Thief Problem

```
private int maxMoneyRecursive( int[] HouseNetWorth, int currentIndex )

    int stealCurrentHouse = HouseNetWorth[currentIndex] + maxMoneyRecursive(HouseNetWorth, currentIndex + 2)
    int skipCurrentHouse = maxMoneyRecursive(HouseNetWorth, currentIndex + 1)

    return Math.max(stealCurrentHouse, skipCurrentHouse)
```

![](../../images/2019-07-23-10-30-07.png)

Also here we can see that we are solving the same problems again and again like MaxMoney(3), MaxMoney(4), MaxMoney(5).

We can optimize it using dynamic programming.

## Top Down approach

```
int maxMoney_TopDown(int[] dp, int[] HouseNetWorth, int currentIndex)

    if( currentIndex >= HouseNetWorth.length) return 0

    if dp[currentIndex] == 0
        
        int stealCurrent = HouseNetWorth[currentIndex] + maxMoney_TopDown(dp, HouseNetWorth, currentIndex + 2)

        int skipCurrent = maxMoney_TopDown(dp, HouseNetWorth, currentIndex + 1)

        dp[currentIndex] = Math.max(stealCurrent, skipCurrent)

    return dp[currentIndex]
```

## Bottom Up approach

```
int maxMoney_BottomUp(int wealth)

    int dp[] = new int[wealth.length + 2]
    dp[wealth.length] = 0

    for int = wealth.length - 1; i >= 0; i--
        dp[i] Math.max(wealth[i] + dp[i+2], dp[i+1])

    return dp[0]
```