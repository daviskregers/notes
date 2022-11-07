# Longest Common Subsequence


```
int findLCSLengthAux(String s1, String s2, int i1, int i2)

    if(i1 == s1.length || i2 == s2.length) // base case
        return 0
        
    int c3 = 0

    if s1.charAt(i1) == s2.charAt(i2) // current char matches
        c3 = 1 + findLCSLengthAux(s1, s2, i1 + 1, i2 + 1)

    int c1 = findLCSLengthAux(s1, s2, i1, i2 + 1)
    int c2 = findLCSLengthAux(s1, s2, i1 + 1, i2)

    return Max(c1, c2, c3)

```

![](../../images/2019-07-23-12-13-50.png)

## Top Down approach

```
int findLCSLengthAux(int[][] dp, String s1, String s2, int i1, int i2)

    if i1 == s1.length || i2 == s2.length
        return 0

    int c3 = 0
    if dp[i1][i2] == -1
        if s1.charAt(i1) == s2.charAt(i2)
            c3 = 1 + findLCSLengthAux(dp, s1, s2, i1 + 1, i2 + 1)
        
        c1 = findLCSLengthAux(dp, s1, s2, i1, i2 + 1)
        c2 = findLCSLengthAux(dp, s1, s2, i1 + 1, i2)

        dp[i1][i2] = Math.max(c1,c2,c3)

    return dp[i1][i2]

```

## Bottom Up approach

```
int findLCSLength(String s1, String s2)

    int[][] dp = new int[s1.length + 1][s2.length + 1]

    for int i = s1.length; i >= 1; i--
        for int j = s2.length; j >= 1; j--
            if s1.charAt(i - 1) == s2.charAt(j - 1)
                dp[i][j] = Math.max(1 + dp[i-1][j-1], dp[i][j+1], dp[i+1][j])
            else
                dp[i][j] - Math.max(dp[i][j+1], dp[i+1][j])
    
    return dp[0][0]

```