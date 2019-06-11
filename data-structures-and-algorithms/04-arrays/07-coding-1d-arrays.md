# Coding 1D arrays

We can create 2 files - `SingleDimensionArray.java` and `SingleDimensionArrayMain.java` where the first one is a class that implements all the logic for arrays and the second is used to run it.

SingleDimensionArray:

```java
package array;

public class SingleDimensionArray {
    int arr[] = null;

    // Constructor
    public SingleDimensionArray(int sizeOfArray)
    {
        arr = new int[sizeOfArray];
        for (int i = 0; i < arr.length; i++) {
            arr[i] = Integer.MIN_VALUE;
        }
    }

    // Print the array
    public void traverseArray() 
    {

        try {
            for( int i = 0; i < arr.length; i++) {
                System.out.print(arr[i] + " ");
            }
        } catch ( Exception e ) {
            System.out.println("Array no longer exists!");
        }

    }

    // Insert value in the Array
    public void insert(int location, int valueToBeInserted) 
    {
        try {

            if( arr[location] == Integer.MIN_VALUE ) {
                arr[location] = valueToBeInserted;
                System.out.println("Successfully inserted " + valueToBeInserted + " at location: " + location);
            } else {
                System.out.println("This cell is already occupied by another value.");
            }

        } catch( ArrayIndexOutOfBoundsException e ) {
            System.out.println("Invalid index to access array!");
        }
    }

    // Access a particular element of an array
    public void accessingCell(int cellNumber)
    {
        try {
            System.out.println(arr[cellNumber]);
        } catch( ArrayIndexOutOfBoundsException e ) {
            System.out.println("Invalid index to access array!");
        }
    }

    // Search for an element in the given Array
    public void searchInAnArray(int valueToSearch) {
        for (int i = 0; i < arr.length; i++) {
            if(arr[i] == valueToSearch) {
                System.out.println("Value found!");
                System.out.println("Index of " + valueToSearch + " is " + i);
                return;
            }
        }
        System.out.println(valueToSearch + " is not found!");
    }

    // Delete value from given Array
    public void deleteValueFromArray(int deleteValueFromThisCell)
    {
        try {
            arr[deleteValueFromThisCell] = Integer.MIN_VALUE;
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Invalid index to access array!");
        }
    }

}
```

SingleDimensionArrayMain

```java
package array;
import array.SingleDimensionArray;

public class SingleDimensionArrayMain {

    public static void main(String[] args) {
        
        System.out.println("Creating a blank array of size 10...");
        SingleDimensionArray sda = new SingleDimensionArray(10);

        System.out.println("Printing the Array...");
        sda.traverseArray();

        System.out.println();
        System.out.println();

        System.out.println("Inserting few values in the array...");
        sda.insert(0,0);
        sda.insert(1,10);
        sda.insert(2,20);
        sda.insert(3,30);
        sda.insert(4,40);
        sda.insert(5,50);
        sda.insert(6,60);
        sda.insert(7,70);
        sda.insert(8,80);
        sda.insert(1,100);
        sda.insert(12,120);

        System.out.println();
        System.out.println();

        System.out.println("Accessing cell number #1");
        sda.accessingCell(1);

        System.out.println();
        System.out.println();

        System.out.println("Searching for 400 in the array...");
        sda.searchInAnArray(400);
        System.out.println("Searching for 40 in the array...");
        sda.searchInAnArray(40);

        System.out.println();
        System.out.println();

        System.out.println("Deleting cell number #3");
        System.out.println("Before deleting:");
        sda.traverseArray();
        sda.deleteValueFromArray(3);
        System.out.println("After deleting:");
        sda.traverseArray();
        
        System.out.println();
        System.out.println();



    }

}
```

Now we can compile and run it:

```
➜  01-array git:(master) ✗ ls array 
SingleDimensionArray.java  SingleDimensionArrayMain.java
➜  01-array git:(master) ✗ javac array/*.java                 
➜  01-array git:(master) ✗ java array.SingleDimensionArrayMain
Creating a blank array of size 10...
Printing the Array...
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 -2147483648 -2147483648 -2147483648 -2147483648 -2147483648 

Inserting few values in the array...
Successfully inserted 0 at location: 0
Successfully inserted 10 at location: 1
Successfully inserted 20 at location: 2
Successfully inserted 30 at location: 3
Successfully inserted 40 at location: 4
Successfully inserted 50 at location: 5
Successfully inserted 60 at location: 6
Successfully inserted 70 at location: 7
Successfully inserted 80 at location: 8
This cell is already occupied by another value.
Invalid index to access array!


Accessing cell number #1
10


Searching for 400 in the array...
400 is not found!
Searching for 40 in the array...
Value found!
Index of 40 is 4


Deleting cell number #3
Before deleting:
0 10 20 30 40 50 60 70 80 -2147483648 After deleting:
0 10 20 -2147483648 40 50 60 70 80 -2147483648 
```