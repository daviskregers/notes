# Recursion vs iteration

|                                       | Recursion | Iteration |
|---------------------------------------|-----------|-----------|
| Space efficient?                      | No        | Yes       |
| Time efficcient?                      | No        | Yes       |
| Ease of code (to solve sub-problems)? | Yes       | No        |

When it comes to space efficiency, the recursion pushes all recursive calls to the memory stack, but in iterations we do not need to store them in the stack, we can use a basic loop.

In time efficiency since recursion uses a memory stack, it will require to use push and pop functions of the memory stack, as well as pointer operations which will take up time. These operations can be avoided when using iterations with a simple loop.

When it comes to ease of code, when we have a problem that can be easily broken up into similar sub-problems, in these kind of cases the recursion is a better approach.