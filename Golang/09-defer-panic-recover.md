# Defer, Panic and Recover

- Defer
    - Used to delay execution of an assignment until function exits
    - Useful to group "open" and "close" functions together
        - Be careful in loops
    - Run in LIFO (last in, first out) order
    - Arguments evaluated at time defer is executed, not at time of called function execution
- Panic
    - Occur when programm cannot continue at all
        - Don't use when file can't be opened, unless it's critical
        - Use for unrecoverable events - cannot obtain TCP port for web server
    - Function will stop executing
        - Deffered functions will still fire
    - If nothging handles panic, program will exit
- Recover
    - Used to recover from panics
    - Only useful in deffered functions
    - The current function will not attemt to continue, but higher functions in call stack will

```go
package main

import (
    "fmt"
    "io/ioutil"
    "log"
    "net/http"
)

func main() {

    fmt.Println("start")
    defer fmt.Println("middle") // execute at the end of the function, before return
    fmt.Println("end")

    // start
    // end
    // middle

    defer fmt.Println("start")
    defer fmt.Println("middle")
    defer fmt.Println("end")

    // Executes in LIFO:
    // end
    // middle
    // start

    res, err := http.Get("http://www.google.com/robots.txt")
    defer res.Body.Close()

    if err != nil {
        log.Fatal(err)
    }

    robots, err := ioutil.ReadAll(res.Body)

    if err != nil {
        log.Fatal(err)
    }

    fmt.Printf("%s\n", robots[0:100])

    //

    defer func() {
        if err := recover(); err != nil {
            log.Println("Error: ", err)
        }
    }()

    a, b := 1, 0
    ans := a / b
    fmt.Println(ans)

    // will not execute this because 1 / 0 threw a panic, stopped execution
    panic("Something bad happened!")

}
```

```go
start
end
User-agent: *
Disallow: /search
Allow: /search/about
Allow: /search/static
Allow: /search/howsearchw
2019/12/25 13:44:16 Error:  runtime error: integer divide by zero
end
middle
start
middle                            
```