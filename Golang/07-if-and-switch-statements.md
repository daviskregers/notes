# If and Switch statements

- If statements
    - initializer
    - comparison operators
    - logical operators
    - short circuiting
    - if - else statements
    - if - else if statements
    - equality and floats
- switch statements
    - switching on a tag
    - cases with multiple tests
    - initializers
    - switches with no tags
    - Fallthrough
    - Type switches
    - Breaking out early

```go
package main

import (
        "fmt"
        "math"
)

func main() {

    // if statements

    if true {
        fmt.Println("The test is true")
    }

    if false {
        fmt.Println("The test is false")
    }

    statePopulations := map[string]int{"California": 39250017}

    if pop, ok := statePopulations["California"]; ok {
        fmt.Println(pop)
    }

    if _, ok := statePopulations["Ohio"]; ok {
        fmt.Println("...")
    }

    if true || false {
        fmt.Println("...")
    }

    if true && true {
        fmt.Println("...")
    }

    myNum := 0.123456789
    if math.Abs(myNum / math.Pow(math.Sqrt(myNum), 2) - 1) < 0.001 {
        fmt.Println("These are the same")
    } else {
        fmt.Println("These are different")
    }

    // switch statements

    switch i := 2+3; i {
        case 1, 5, 10:
            fmt.Println("one, five or ten")
        case 2, 4, 6:
            fmt.Println("two, four or six")
        default:
            fmt.Println("another number")
    }

    i := 10
    switch {
        case i <= 10:
            fmt.Println("less than or equal to ten")
            fallthrough // execute the statements in the next case as well
        case i >= 20:
            fmt.Println("less than or equal to twenty")
        default:
            fmt.Println("greater than twenty")
    }

    // type switch

    var j interface{} = 1 // can take any type of data
    switch j.(type) {
    case int:
        fmt.Println("j is an int")
        break
        fmt.Println("This this wont print")
    case float64:
        fmt.Println("j is a float64")
    case string:
        fmt.Println("j is a string")
    default:
        fmt.Println("j is another type")
    }

}
```

```go
The test is true
39250017
...
...
These are the same
one, five or ten
less than or equal to ten
less than or equal to twenty
j is an int
```