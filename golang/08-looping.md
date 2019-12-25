# Looping

- For statements
    - Simple loops
        - for initializer; test; incrementer {}
        - for test {}
        - for {}
    - Exiting early
        - break
        - continue
        - labels
    - Looping over collections
        - arrays, slices, maps, strings, channels
        - for k, v := range collection {}

```go
package main

import "fmt"

func main() {

    // for loops
    for i := 0; i < 5; i++ {
        fmt.Println(i)
    }

    for i,j := 0, 0; i < 5; i, j = i+1, j+2 {
        fmt.Println(i, j)
    }

    i := 0
    for ; i < 5; i++ {
        // ...
    }
    fmt.Println(i)

    // break

    for {
        fmt.Println(i)
        i++
        if i == 10 {
            break
        }
    }

    // continue

    for i := 0; i < 10; i++ {
        if i % 2 == 0 {
            continue
        }
        fmt.Println(i)
    }

    //

    Loop:
    for i := 1; i <= 3; i++ {
        for j := 1; j <= 3; j ++ {
            fmt.Println(i * j)
            if i * j >= 3 {
                break Loop // break out of both loops at once
            }
        }
    }

    // collections with loops

    s := []int{1,2,3}
    for key, value := range s {
        fmt.Println(key, value)
    }


        statePopulations := map[string]int{
                "California":   39250017,
                "Texas":        27862596,
                "Florida":      20612439,
                "New York":     19745289,
                "Pennsylvania": 12802503,
                "Illinois":     12801539,
                "Ohio":         11614373,
        }

    for k, v := range statePopulations {
        fmt.Println(k, v)
    }

    for k := range statePopulations {
        fmt.Println(k)
    }

    for _, v := range statePopulations {
        fmt.Println(v)
    }

    st := "Hello Go!"
    for k, v := range st {
        fmt.Println(k, v, string(v))
    }

}
```

```go
0
1
2
3
4
0 0
1 2
2 4
3 6
4 8
5
5
6
7
8
9
1
3
5
7
9
1
2
3
0 1
1 2
2 3
New York 19745289
Pennsylvania 12802503
Illinois 12801539
Ohio 11614373
California 39250017
Texas 27862596
Florida 20612439
California
Texas
Florida
New York
Pennsylvania
Illinois
Ohio
39250017
27862596
20612439
19745289
12802503
12801539
11614373
0 72 H
1 101 e
2 108 l
3 108 l
4 111 o
5 32  
6 71 G
7 111 o
8 33 !
```