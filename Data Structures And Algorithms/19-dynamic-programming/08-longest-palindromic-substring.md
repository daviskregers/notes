# Longest palindromic substring


```
int lps_aux(String string, int startIndex, int endIndex)

    if startIndex > endIndex // don't need to traverse more than 1/2 string
        return 0

    if startIndex == endIndex // only one character
        return 1

    int c1 = 0

    if(string.charAt(startIndex) == string.charAt(endIndex))
        
        // add 2 to the existing known palindrome length only if remaining string is a palindrom too
        int remainingLength = endIndex - startIndex - 1

        if remainingLength == lpsaux(string, startIndex + 1, endIndex - 1)
            c1 = remainingLength + 2

    int c2 = lps_aux(string, startIndex + 1, endIndex)
    int c3 = lps_aux(string, startIndex, endIndex - 1)

    return Math.max(c1, c2, c3)
        
```

![](../../images/2019-07-23-12-28-40.png)

## Top down approach

```
int lps_aux(int[][] dp, String string, int startIndex, int endIndex)

    if startIndex > endIndex
        return 0

    if startIndex == endIndex
        return 1

    if dp[startIndex][endIndex] == null
        int c1 = 0
        if string.charAt(startIndex == string.charAt(endIndex))
            int remainingLength = endIndex - startIndex - 1

            if remainingLength == lpsaux(dp, string, startIndex + 1, endIndex - 1)
                c1 = remainingLength + 2
        
        int c2 = lps_aux(dp, string, startIndex + 1, endIndex)
        int c3 = lps_aux(dp, string, startIndex, endIndex - 1)

        dp[startIndex][endIndex] = Math.max(c1,c2,c3)

    return dp[startIndex][endIndex]


## Bottom up approach

```
int findLPSLength(String st)

    int [][] dp = new int[st.length][st.length]

    for int col = 0; col < st.length; col++
        for int row = st.length; row >= 0; row--
            
            if row > col
                dp[row][col] = 0
            else if row == col
                dp[row][col] = 1
            else
                if st.charAt(row) == st.charAt(col)
                    int expectedSubstringLength = col - row - 1
                    int stringLengthToBeUsed = dp[row + 1][col-1] == expectedSubstringLength ? dp[row + 1][col]
                else
                    dp[row][col]= Math.max(dp[row][col - 1], dp[row + 1][col])
    
    return dp[0][st.length - 1]
```