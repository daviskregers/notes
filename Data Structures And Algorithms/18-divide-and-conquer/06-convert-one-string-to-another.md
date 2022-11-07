# Convert one string to another

We are given strings s1 and s2. We need to convert s2 into s1 by deleting, inserting or replacing characters. Write a function to calculate the count of the minimum number of edit operations.

Example:

    s1 = "catch"
    s2 = "carch"
    Output: 1
    Explanation: We just need to replace r.

    s1 = "table"
    s2 = "tbres"
    Output: 3
    Explanation: We need to insert a at second position, replace r with l. Delete s.

We can divide the problem into sub-problems by firstly considering the whole string, then a substring, then a substring of that string and so on.

```
private int findMinOperationsAux(String s1, String s2, int i1, int i2)

    if i1 == s1.length // if we have reached the end of s1, so rest of the characters of s2 needs to be deleted.
        return s2.length - i2
    if i2 == s2.length // we have reached the end of s2, so rest of the characters needs to be inserted in s2
        return s1.length - i1
    if s1.charAt(i1) == s2.charAt(i2) // if string have a matching character, recursively match for the remaining lengths
        return findMinOperationsAux(s1, s2, i1+1, i2+1)

    int c1 = 1 + findMinOperationsAux(s1,s2,i1 + 1, i2) // insertion
    int c2 = 1 + findMinOperationsAux(s1,s2,i1, i2+1) // deletion
    int c3 = 1 + findMinOperationsAux(s1,s2,i1 + 1, i2 + 1) // replacement

    return Min(c1, c2, c3)
```