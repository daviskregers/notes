# What is an array

Array is a data structure consisting of a collection of elements, each identified by array index. An array is stored in such way that the position of each element can be computed from it's index cell by a mathematical formula.

Array properties:
- Array can store data of specified data type (integer, long, double).
- It has contiguous memory location
- Every cell of an Array has an unique index
- Indexes start with 0
- Size of array needs to be specified mandatorily and can not be modified.

## Why do we need an array?

Problem: We want to store 1 million similar data types in memory.

We can create 1 million variables of a primitive data structure like integer, but maintaining it would be borderline impossible.

Instead, we can declare an array with a length of 1 million. Then we need only to reference the cell number of the array and we can access that cell.
