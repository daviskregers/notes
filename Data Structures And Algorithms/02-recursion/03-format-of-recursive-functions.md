# Format of recursive functions

A recursive function is based on two elements:
- Recursive case. Case where the function recurs.
- Base case. Case where the function doesnt recur.

Example:

```

SampleRecursion (parameter) 
{
    if ( base case is satisfied )
        return some base case value
    else 
        SampleRecusion(modified parameter)
}

```