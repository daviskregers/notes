# Longest common subsequence

We are given two strings s1 and s2. We need to find the length of the longes subsequence which is common in both of the strings. Subsequence is a sequence that can be derived from another sequence by deleting some elements without changing the order of the remaining elements.

Example:

    s1 = elephant
    s2 = eretpat
    Output: 5
    Explanation: The longest substring is eepat

    s1 = houdini
    s2 = hdupti
    Output: 3
    Explanation: The longest substring is hui

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