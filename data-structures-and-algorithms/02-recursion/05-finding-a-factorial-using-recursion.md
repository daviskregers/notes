# Finding a factorial using recursion

Factorial definition:
- It can only be found for non-negative integers
- Denoted by n!
- Is the product of all positive integers from 1 to n

Examples:
5! = 5 * 4 * 3 * 2 * 1 = 120
10! = 10 * 9 * 8 * 7 * 6 * 5 * 4 * 3 * 2 * 1 = 3628800

```
Factorial(n):
    if n == 0
        return 1
    return (n * factorial(n-1))
```