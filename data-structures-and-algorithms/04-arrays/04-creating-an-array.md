# Creating an array

When we create an array, first thing we do it declare it.

It creates a reference variable like `arr` that basically gives a name to the array.

The second thing is array instantiation, which allocates memory for the array in RAM. Then it updates the reference variable with an address of the first cell of the array.

This is used because we can use this address to reference each cell of the array. For example if the first cell address is `X102`, then we can find the second by using `X102 + 1`, the third `X102 + 2` and so on.

The last step is to initialize the array - which basically means to assign values to the array cells.

------------------

In java we can declare 1D arrays by doing the following:

```java
dataType[] name
int[] arr1
float[] arr2
char[] arr3
```

Then we can instantiate it:

```java
arrayRefVar = new datatype[size]
arr = new int[5]
```

Then we can initialize it:

```java
a[0] = 10;
a[1] = 20;
a[2] = 30;
a[3] = 40;
a[4] = 50;
```

We can combine all of these steps into one line by using:

```java
int a[] = {10,20,30,40,50};
```

-----------

Time complexity when declaring, instantiating, initializing 1D arrays.

```java
int[] arr -------------------------------------- O(1)
arr = new int[5] ------------------------------- O(1)
arr[0] = 10; -------------------------- O(1) -|
arr[1] = 20; -------------------------- O(1) -|
arr[2] = 30; -------------------------- O(1) -|- O(n)
arr[3] = 40; -------------------------- O(1) -|
arr[4] = 50; -------------------------- O(1) -|

int arr[] = {10,20,30,40,50} ------------------- O(1)
```