# Functions

- Basic syntax
    - func foo() { ... }
- Parameters
    - Comma delimited list of variables and types
        - func foo(bar string, baz int)
    - Parameters of same type list type once
        - func foo(bar, baz int)
    - When pointers are passed in, the function can change the value in the caller
        - This is always true for data of slices and maps
    - Use variadic parameters to send list of same types in
        - Must be last parameter
        - Received as a slice
        - func foo (bar string, baz ...int)
- Return values
    - Single return values just list type
        - func foo() int
    - multiple return value list types surrounded by parenttheses
        - func foo() (int, error)
        - The (result type, error) paradigm is a very common idiom
    - Can use named return values
        - Initializes returned variable
        - Return using return keyword on it's own
    - Can return addresses of local variables
        - Automatically promoted from local memory (stack) to shared memory (heap)
- Anonymous functions
    - Functions don't have names if they are:
        - Immediately invoked
            - func() {...}()
        - Assigned to a variable or passed as an argument to function
            - a := func() {...}
            - a()
- Functions as types
    - Can assign functions to variables or use as arguments and return values in functions
    - Type signature is like function signature, with no paramter names
        - var f func(string, string, int) (int, error)
- Methods
    - Function that executes in context of a type
    - Format
        - func (g greeter) greet() {
            ...
        }
    - Receiver can be value or pointer
        - Value receiver gets copy of type
        - Pointer receiver gets pointer to type

```go
package main

import (
    "fmt"
)

func sayMessage(msg string, idx int) {
    fmt.Println(msg, idx)
    msg = "123"
}

func sayGreeting(greeting *string, name *string) {
    fmt.Println(*greeting, *name) // Hello Stacey
    *name = "Ted"
    fmt.Println(*name) // Ted
}

func sum(values ...int) (result int) {
    fmt.Println(values)
    for _, v := range values {
        result += v
    }
    return
}

func divide(a, b float64) (float64, error) {
    if b == 0.0 {
        return 0.0, fmt.Errorf("Cannot divide by zero")
    }
    return a / b, nil
}

func main() {
    var message string = "Hello Go!"
    for i := 0; i < 5; i++ {
        sayMessage(message, i)
    }
    fmt.Println(message) // Hello Go!, not 123

    // with pointers

    greeting := "Hello"
    name := "Stacey"
    sayGreeting(&greeting, &name)
    fmt.Println(name) // Ted

    // variadic parameters

    s := sum(1, 2, 3, 4, 5)
    fmt.Println("The sum is ", s)

    // 

    d, err := divide(5.0, 0.0)
    if err != nil {
        fmt.Println(err)
    }
    fmt.Println(d) 

    // anonymous functions

    func() {
       fmt.Println("Hello Anonymous Go!")
    }() // these () invoke the function

    var f func() = func() {
        fmt.Println("Hello Go!")
    }
    f()

    var divide func(float64, float64) (float64, error)
    divide = func(a, b float64) (float64, error) {
        // ...
        return 0, nil
    }
    divide(0.0, 0.0)

    // methods

    g := greeter {
        greeting: "Hello",
        name: "Go",
    }
    g.greet()
    fmt.Println("The new name is", g.name)
    g.greets()
    fmt.Println("The new name is", g.name)

}

type greeter struct {
    greeting string
    name string
}

func (g greeter) greet() {
    fmt.Println(g.greeting, g.name)
    g.name = "not Go"
}

func (g *greeter) greets() {
    fmt.Println(g.greeting, g.name)
    g.name = "not Go"
}
```

```go
Hello Go! 0
Hello Go! 1
Hello Go! 2
Hello Go! 3
Hello Go! 4
Hello Go!
Hello Stacey
Ted
Ted
[1 2 3 4 5]
The sum is  15
Cannot divide by zero
0
Hello Anonymous Go!
Hello Go!
Hello Go
The new name is Go
Hello Go
The new name is not Go
```