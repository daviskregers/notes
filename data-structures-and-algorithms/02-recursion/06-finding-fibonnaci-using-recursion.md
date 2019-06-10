# Finding Fibonacci series using Recursion

Fibonacci series:
- A series of numbers in which each number is the sum of the two preceding numbers.
- The first 2 numbers by the definition are 0 and 1

Example:
- 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...

```
fib(n)

    if (n < 1)
        return error message
    else if n == 1 or n == 2
        return n - 1
    else 
        return fib(n - 1) + fib(n - 2)