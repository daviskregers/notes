# Pointers

- Creating pointers
    - Pointer types use an asterisk (*) as a prefix to type pointed to
        - *int a pointer to an integer
    - Use the addressof operator (&) to get an address of variable
- Dereferencing pointers
    - dereference a pointer by preceding with an asterisk (*)
    - Complex types (e.g.) structs are automatically dereferenced
- Create pointers to objects
    - Can use the addressof operator (&) if value type already exists
        - ms := myStruct{foo: 42}
        - p := &ms
    - Use addressof operator before initializer
        - &myStruct{foo: 42}
    - Use the new keyword
        - Can't initialize fields at the same time
- Types with internal pointers
    - All assignment operations in Go are copy operations
    - Slices and maps contain internal pointers, so copies point to same underlying data

```go
package main

import (
    "fmt"
)

func main() {

    var a int  = 42
    var b *int = &a
    a = 27
    fmt.Println(a) // 27
    fmt.Println(&a) // 0xc0000180d8 (reference)
    fmt.Println(b)  // 0xc0000180d8
    fmt.Println(a)  // 27
    fmt.Println(*b) // 27 (dereference)

    *b = 14
    fmt.Println(a, *b) // 14 14

    c := [3]int{1,2,3}
    d := &c[0]
    e := &c[1] 
    fmt.Println("%v %p %p\n", c, d, e)

    // for pointer arithmetic, we can lookup `unsafe` package

    var ms *myStruct
    ms = &myStruct{foo: 42}
    fmt.Println(ms)

    var mz *myStruct
    fmt.Println(mz) // nil
    mz = new(myStruct)
    fmt.Println(mz) // 0

    var mx *myStruct
    mx = new(myStruct)
    (*mx).foo = 42
    fmt.Println((*mx).foo) // 42
    fmt.Println(mx.foo) // 42

}

type myStruct struct {
    foo int
}
```

```go
27
0xc0000180d8
0xc0000180d8
27
27
14 14
%v %p %p
 [1 2 3] 0xc000014180 0xc000014188
&{42}
<nil>
&{0}
42
42
```