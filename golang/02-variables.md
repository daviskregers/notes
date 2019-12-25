# Variables

There are 3 ways to declare variables in go.

```go
package main

import (
        "fmt"
)

func main() {

        var i int
        i = 42
        i = 27
        fmt.Println(i)

        var j int = 42
        fmt.Println(j)

        k := 12
        fmt.Println(k)

}
```

Another method is to declare variables at package level.

```go
var l float32 = 56

func main() {
    fmt.Println(l)
}
```

We can also define a block of variables.

```go
var (                                         
        actorName       string = "Elisabeth Sladen"
        companion       string = "Sarah Jane Smith"
        doctorNumber    int    = 3
        season          int    = 11
)
```

## Redeclare variables

In go we can't really redeclare variables, but we can `shadow` them. Which means, if the variable is declared in a higher level scope, we can redeclare it in a lower level scope.

```go
var l float32 = 56

func main() {
    fmt.Println(l)
    var l int = 42
    fmt.Println(l)

    var m int = 26
    // var m float32 = 12 -- will throw an error
}
```

The output will be

```go
56
42
```

## Other interesting things about variables

- They always have to be used.

When you are declaring and variable that is not used, the compiler will throw an error:

```
$variable declared and not used
```

- Visibility
    - lower case first letter variables are used for package scope
        - any file at that package can access the variable
    - upper case first letter to export
        - exported from the package, globally visible
    - no private scope
        - you can't scope variable to the scope itself, but you can declare it in a block and scope to it.

- Naming conventions

    - Pascal or camelCase
        - Capitalize acronyms (HTTP, URL)
    - As short as reasonable
        - longer names for longer lives

- Conversion

    - destinationType(variable)
    - use strconv package for strings

```go
j = float32(l)
fmt.Printf("%v, %T\n", j, j)

l = int(j)
fmt.Printf("%v, %T\n", l, l)

var m int = 42
fmt.Printf("%v, %T\n", m, m)

var n string
n = string(m)
fmt.Printf("%v, %T\n", n, n) // will result in `*`

n = strconv.Itoa(m)
fmt.Printf("%v, %T\n", n, n) // will result to `42`
```

```go
42, float32
42, int
42, int
*, string
42, string
```