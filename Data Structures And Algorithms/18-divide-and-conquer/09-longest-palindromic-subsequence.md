# Longest palindromic subsequence

We are given a string S. We need to find the length of it's palindromic subsequence LPS in the given S string. Palindrome is a string that reads the same backwards as well as forwards and can be of odd or even length.

Example:

    INPUT: ELRMENMET
    Output: 5
    LPS is EMEME

    INPUT AMEEMWMEA
    Output: 6
    LPS IS AMEEMA

```
int LPSAux( String st, int startIndex, int endIndex )
    if startIndex > endIndex // dont need to traverse more than 1/2 of the string
        return 0

    if startIndex == endIndex // there is only 1 character
        return 1

    int count1 = 0

    if st.charAt(startIndex == st.charAt(endIndex))
        count1 = 2+ LPSAux(st, startIndex + 1, endIndex - 1)

    int count2 = LPSAux(st, startIndex + 1, endIndex)
    int count3 = LPSAUx(st, startIndex, endIndex - 1)

    return Max(count1, count2, count3)
```