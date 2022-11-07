# Coding 2D arrays

We can create 2 files - `TwoDimensionalArray.java` and `TwoDimensionalArrayMain.java` where the first one is a class that implements all the logic for arrays and the second is used to run it.

TwoDimensionalArray:

```java
package array;

public class TwoDimensionalArray {

    int arr[][] = null;

    // Constructor
    public TwoDimensionalArray(int numberOfRows, int numberOfColumns)
    {
        this.arr = new int[numberOfRows][numberOfColumns];
        for( int row = 0; row < arr.length; row++) {
            for( int col = 0; col < arr[row].length; col++) {
                arr[row][col] = Integer.MIN_VALUE;
            }
        }
    }

    // Traverse array
    public void traverseArray() 
    {
        try {

            System.out.println("Printing the array now...");

            for(int row = 0; row < arr.length; row++) {
                for(int col = 0; col < arr[row].length; col++) {
                    System.out.print(arr[row][col] + " ");
                }
                System.out.println();
            }
            System.out.println("\n");
        } catch ( Exception e ) {
            System.out.println("Array does not exist");
        }
    }

    // Insert value
    public void insertValueInArray(int row, int col, int value)
    {
        try {
            if(arr[row][col] == Integer.MIN_VALUE) {
                arr[row][col] = value;
                System.out.println("Successfully inserted " + value + " in the array");
            } else {
                System.out.println("This cell is already occupied by another value");
            }
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Invalid index to access array!");
        }
    }

    // access cell
    public void accessCell(int row, int col) 
    {
        System.out.println("\nAccessing row " + row +", col " + col);
        try {
            System.out.println("Cell value is: " + arr[row][col]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Invalid index to access array!");
        }
    }

    // search value
    public void searchValue(int value) 
    {

        System.out.println("\n Searching for value " + value);
        for(int row = 0; row < arr.length; row++) {
            for(int col = 0; col < arr[row].length; col++) {
                if(arr[row][col] == value) {
                    System.out.println("Value has been found at location [" + row + "][" + col + "]" );
                    return;
                }
            }
        }

        System.out.println("The value was not found");

    }

    // delete value
    public void deleteValue(int row, int col) 
    {
        System.out.println("Deleting value from row " + row + ", col " + col);
        
        try {
            System.out.println("Successfully deleted: " + arr[row][col]);
            arr[row][col] = Integer.MIN_VALUE;
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Invalid index to access array!");
        }

    }

    // delete entire array
    public void deleteArray()
    {
        arr = null;
        System.out.println("Array has been deleted");
    }



}
```

TwoDimensionalArrayMain

```java
package array;
import array.TwoDimensionalArray;

public class TwoDimensionalArrayMain {

    public static void main(String[] args) {

        System.out.println("Creating a blank array of size 5x5");
        TwoDimensionalArray sda = new TwoDimensionalArray(5,5);
        sda.traverseArray();

        sda.insertValueInArray(0,2, 10000001);
        sda.traverseArray();
        sda.insertValueInArray(0,2, 10000001);
        sda.traverseArray();

        sda.accessCell(0,2);
        sda.accessCell(6,2);
        sda.accessCell(2,2);

        sda.searchValue(10);
        sda.searchValue(Integer.MIN_VALUE);
        sda.searchValue(10000001);

        sda.deleteValue(0,2);
        sda.traverseArray();

        sda.deleteArray();
        sda.traverseArray();

    }

}
```

Now we can compile and run it:

```
➜  02-2d-array git:(master) ✗ javac array/*.java && java array.TwoDimensionalArrayMain
Creating a blank array of size 5x5
Printing the array now...
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 


Successfully inserted 10000001 in the array
Printing the array now...
-2147483648 -2147483648 10000001 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 


This cell is already occupied by another value
Printing the array now...
-2147483648 -2147483648 10000001 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 



Accessing row 0, col 2
Cell value is: 10000001

Accessing row 6, col 2
Invalid index to access array!

Accessing row 2, col 2
Cell value is: -2147483648

 Searching for value 10
The value was not found

 Searching for value -2147483648
Value has been found at location [0][0]

 Searching for value 10000001
Value has been found at location [0][2]
Deleting value from row 0, col 2
Successfully deleted: 10000001
Printing the array now...
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 
-2147483648 -2147483648 -2147483648 -2147483648 -2147483648 


Array has been deleted
Printing the array now...
Array does not exist
```