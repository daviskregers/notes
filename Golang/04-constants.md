# Constants

- Immutable, but can be shadowed
- Replaced by the compiler at compile time
    - Value bust be calculable at compile time
- Named like variables
    - PascalCase for exported constants
    - camelCase for internal constants
- Typed constants work like immutable variables
    - can interoperate only with same type
- Untyped constants work like literals
    - Can interoperate with similar types
- Enumerated Constants
    - Special symbol iota allows related constants to be created easily
    - Iota starts at 0 in each const block and increments by one
    - Watch out of constant values that m,atch zero values for variables
- Enumverated expressions
    - Operations that can be determined at compile time are allowed
        - Arithmetic
        - Bitwise operations
        - Bitshifting

```go

import (
        "fmt"
)

const e int16 = 27

const h = iota // Enumerated constant, counter
const (
        i = iota
        j = iota
        k = iota
)
const (
        _ = iota // default, error / zero value
        catSpecialist
        dogSpecialist
        snakeSpecialist
)

const ( // enumerated expressions
        _ = iota // ignore first value by assigning to blank identifier
        KB = 1 << (10 * iota)
        MB
        GB
        TB
        PB
        EB
        ZB
        YB
)

const (
        isAdmin = 1 << iota
        isHeadquarters
        canSeeFinancials

        canSeeAfrica
        canSeeAsia
        canSeeEurope
        canSeeNorthAmerica
        canSeeSouthAmerica
)

func main() {

        // typed constants

        const a int = 42
        const b string = "foo"
        const c float32 = 3.14
        const d bool = true
        const e int = 34

        fmt.Printf("%v, %T\n", a, a)
        fmt.Printf("%v, %T\n", b, b)
        fmt.Printf("%v, %T\n", c, c)
        fmt.Printf("%v, %T\n", d, d)
        fmt.Printf("%v, %T\n", e, e) // 34, int

        // untyped constants

        const f = 42
        const g int16 = 27
        fmt.Printf("%v, %T\n", f, f) // int
        fmt.Printf("%v, %T\n", g, g) // int16
        fmt.Printf("%v, %T\n", f + g, f + g) // int16

        // enumerated constants

        fmt.Printf("%v, %T\n", h, h) // 0, int
        fmt.Printf("%v, %T\n", i, i) // 0, int
        fmt.Printf("%v, %T\n", j, j) // 1, int
        fmt.Printf("%v, %T\n", k, k) // 2, int

        fmt.Printf("%v, %T\n", catSpecialist, catSpecialist) // 1, int
        fmt.Printf("%v, %T\n", dogSpecialist, dogSpecialist) // 2, int
        fmt.Printf("%v, %T\n", snakeSpecialist, snakeSpecialist) // 3, int

        var spacialistType int
        fmt.Printf("%v\n", spacialistType == catSpecialist) // false


        // enumerated expressions

        fmt.Printf("%v, %T\n", KB, KB) // 1024, int 
        fmt.Printf("%v, %T\n", MB, MB) // 1048576, int 
        fmt.Printf("%v, %T\n", GB, GB) // 1073741824, int 

        var roles byte = isAdmin | canSeeFinancials | canSeeEurope
        fmt.Printf("%b\n", roles) // 100101
        fmt.Printf("Is Admin? %v\n", isAdmin & roles == isAdmin) // true
        fmt.Printf("Is HQ? %v\n", isHeadquarters & roles == isHeadquarters) // false

}
```

```go
42, int
foo, string
3.14, float32
true, bool
34, int
42, int
27, int16
69, int16
0, int
0, int
1, int
2, int
1, int
2, int
3, int
false
1024, int
1048576, int
1073741824, int
100101
Is Admin? true
Is HQ? false
```