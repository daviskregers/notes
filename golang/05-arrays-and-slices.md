# Arrays and slices

- Arrays
    - Collection of items with same type
    - Fixed size
    - Declaration styles
        - a := [3]int{1,2,3}
        - a := [...]int{1,2,3}
        - var a [3]int
    - Access via zero based index
        - a := [3]int {1, 3, 5} // a[1] == 3
    - len function returns size of array
    - Copies refer to different underlying data
- Slices
    - Backed by array
    - Creation styles
        - Slice an existing array or slice
        - Literal style
        - Via function make
            - a := make([]int, 10) // create slice with capacity and length == 10
            - a := make([], 10, 100) // slice with length == 10 and capacity == 100
    - len function returns length of slice
    - cap function returns length of underlying array
    - append function to add elements to slice
        - may cause expensive copy operations if underlying array is too small
    - Copies refer to same underlying array

```go
package main

import (
        "fmt"
)

func main() {

        // arrays
        grades := [3]int{97, 85, 93}
        fmt.Printf("Grades: %v\n", grades)

        // create array that is just large enough to hold the data
        grades2 := [...]int{97, 85, 93}
        fmt.Printf("Grades2: %v\n", grades2)


        var students [3]string
        fmt.Printf("Students %v\n", students)
        students[0] = "Lisa"
        fmt.Printf("Students %v\n", students)
        students[1] = "Ahmed"
        fmt.Printf("Students %v\n", students)
        students[2] = "Arnold"
        fmt.Printf("Students %v\n", students)
        fmt.Printf("Student #1: %v\n", students[0])
        fmt.Printf("Student #2: %v\n", students[1])
        fmt.Printf("Student #3: %v\n", students[2])
        fmt.Printf("Number of Students: %v\n", len(students))

        var identityMatrix [3][3]int = [3][3]int{
                [3]int{1,0,0},
                [3]int{0,1,0},
                [3]int{0,0,1},
        }
        fmt.Println(identityMatrix)

        var identityMatrix2 [3][3]int
        identityMatrix2[0] = [3]int{1,0,0}
        identityMatrix2[1] = [3]int{0,1,0}
        identityMatrix2[2] = [3]int{0,0,1}
        fmt.Println(identityMatrix2)

        // you create copies not point to the same data
        a := [...]int{1,2,3}
        b := a
        b[1] = 5
        fmt.Println(a) // [1 2 3]
        fmt.Println(b) // [1 5 3]

        // slices

        s := []int{1,2,3}
        fmt.Println(s)
        fmt.Printf("Length: %v\n", len(s))
        fmt.Printf("Capacity: %v\n", cap(s))

        // slices do point to the same underlying data
        s1 := s
        s1[1] = 5
        fmt.Println(s) // [1 5 3]
        fmt.Println(s1) // [1 5 3]

        s2 := [...]int{1,2,3,4,5,6,7,8,9,10}
        s3 := s2[:]   // slice of all elements, [1 2 3 4 5 6 7 8 9 10]
        s4 := s2[3:]  // slice from 4th element to end, [4 5 6 7 8 9 10]
        s5 := s2[:6]  // slice first 6 elements, [1 2 3 4 5 6]
        s6 := s2[3:6] // slice the 4th, 5th, 6th elements, [4 5 6]

        s2[5] = 42  // now s2, s5, s6 has 6th element as 42
        fmt.Println(s2)
        fmt.Println(s3)
        fmt.Println(s4)
        fmt.Println(s5)
        fmt.Println(s6)

        // make function

        ss := make([]int, 3, 100) // type, size
        fmt.Println(ss) // [0 0 0]
        fmt.Printf("Length: %v\n", len(ss)) // 3
        fmt.Printf("Capacity: %v\n", cap(ss)) // 100

        //

        sa := []int{}
        fmt.Println(sa) // []
        fmt.Printf("Length: %v\n", len(sa)) // 0
        fmt.Printf("Capacity: %v\n", cap(sa)) // 0
        sa = append(sa, 1)
        fmt.Println(sa) // [1]
        fmt.Printf("Length: %v\n", len(sa)) // 1
        fmt.Printf("Capacity: %v\n", cap(sa)) // 1
        sa = append(sa, 2,3,4,5,6)
        fmt.Println(sa) // [1 2 3 4 5 6]
        fmt.Printf("Length: %v\n", len(sa)) // 6
        fmt.Printf("Capacity: %v\n", cap(sa)) // 6

        // concatenate slices

        sa = append(sa, []int{2,3,4,5,6}...)
        fmt.Println(sa) // [1 2 3 4 5 6 2 3 4 5 6]
        fmt.Printf("Length: %v\n", len(sa)) // 11
        fmt.Printf("Capacity: %v\n", cap(sa)) // 12

        // stack operations

        st := []int{1, 2, 3, 4, 5}
        fmt.Println(st)
        st1 := st[:len(st)-1]
        fmt.Println(st1)

        // remove elements from middle
        sm := append(st[:2], st[3:]...)
        fmt.Println(sm)

        // be careful when dealing with these situations
        // may cause unexpected results
        fmt.Println(st) // [1 2 3 4 5 5]

}
```

```go
Grades: [97 85 93]
Grades2: [97 85 93]
Students [  ]
Students [Lisa  ]
Students [Lisa Ahmed ]
Students [Lisa Ahmed Arnold]
Student #1: Lisa
Student #2: Ahmed
Student #3: Arnold
Number of Students: 3
[[1 0 0] [0 1 0] [0 0 1]]
[[1 0 0] [0 1 0] [0 0 1]]
[1 2 3]
[1 5 3]
[1 2 3]
Length: 3
Capacity: 3
[1 5 3]
[1 5 3]
[1 2 3 4 5 42 7 8 9 10]
[1 2 3 4 5 42 7 8 9 10]
[4 5 42 7 8 9 10]
[1 2 3 4 5 42]
[4 5 42]
[0 0 0]
Length: 3
Capacity: 100
[]
Length: 0
Capacity: 0
[1]
Length: 1
Capacity: 1
[1 2 3 4 5 6]
Length: 6
Capacity: 6
[1 2 3 4 5 6 2 3 4 5 6]
Length: 11
Capacity: 12
[1 2 3 4 5]
[1 2 3 4]
[1 2 4 5]
[1 2 4 5 5]
```