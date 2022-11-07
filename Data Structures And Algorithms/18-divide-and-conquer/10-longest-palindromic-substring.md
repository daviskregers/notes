# Longes palindromic substring

We are given a string S. We need to find the length of it's Longes Palindromic Sunstring (LPS).

Example:

    Input: ABCYRCFBTUA
    Palindromic subsequence: ABCYCBA
    Palindromic substring: A

    Input: ABCCBUA
    Output: 4
    Explanation: LPS is BCCB

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