# Goroutines

- Creating goroutines
    - Use `go` keyword in front of function call
    - When using anonymous functions, pass data as local variables
- Synchronization
    - Use sync.WaitGroup to wait for groups of goroutines to complete
    - Use sync.Mutex and sync.RWMutes to protect data access
- Parallelism
    - By default, Go will use CPU threads equal to available cores
    - Change with runtime.GOMAXPROCS
    - More threads can increase performance, but too many can slow it down
- Best Practices
    - Don't create goroutines in libraries
        - Let consumer control concurrency
    - When creating a goroutine, know how it will end
        - Avoids subtle memory leaks
    - Check for race conditions at compile time
        ```
        ➜  daviskregers git:(master) ✗ go run -race ./13_goroutines/Main.go
        Hello #0
        ==================
        WARNING: DATA RACE
        Write at 0x0000005fe178 by goroutine 8:
        main.increment()
            /home/davis/projects/learning/golang/src/github.com/daviskregers/13_goroutines/Main.go:46 +0x5a

        Previous read at 0x0000005fe178 by goroutine 7:
        main.sayHello()
            /home/davis/projects/learning/golang/src/github.com/daviskregers/13_goroutines/Main.go:35 +0x3e

        Goroutine 8 (running) created at:
        main.main()
            /home/davis/projects/learning/golang/src/github.com/daviskregers/13_goroutines/Main.go:17 +0x80

        Goroutine 7 (finished) created at:
        main.main()
            /home/davis/projects/learning/golang/src/github.com/daviskregers/13_goroutines/Main.go:16 +0x68
        ==================
        Hello #1
        Hello #2
        Hello #3
        Hello #4
        Hello #5
        Hello #6
        Hello #7
        Hello #8
        Hello #9
        Threads: 8
        Hello #10
        Hello #11
        Hello #12
        Hello #13
        Hello #14
        Hello #15
        Hello #16
        Hello #17
        Hello #18
        Hello #19
        Found 1 data race(s)
        exit status 66

        ```

```go
package main

import (
        "fmt"
        "runtime"
        "sync"
)

var wg = sync.WaitGroup{}
var counter = 0
var m = sync.RWMutex{}

func main() {
    for i := 0; i < 10; i++ {
        wg.Add(2)
        go sayHello()
        go increment()
    }
    wg.Wait()

   // 
   fmt.Printf("Threads: %v\n", runtime.GOMAXPROCS(-1))
   for i := 0; i < 10; i++ {
       wg.Add(2)
       m.RLock()
       go sayHelloM()
       m.Lock()
       go incrementM()
   }
   wg.Wait()

}

func sayHello() {
    fmt.Printf("Hello #%v\n", counter)
    wg.Done()
}

func sayHelloM() {
    fmt.Printf("Hello #%v\n", counter)
    m.RUnlock()
    wg.Done()
}

func increment() {
    counter++
    wg.Done()
}

func incrementM() {
    counter++
    m.Unlock()
    wg.Done()
}
```

```go
Hello #2
Hello #4
Hello #0
Hello #2
Hello #5
Hello #5
Hello #7
Hello #8
Hello #8
Hello #9
Threads: 8
Hello #10
Hello #11
Hello #12
Hello #13
Hello #14
Hello #15
Hello #16
Hello #17
Hello #18
Hello #19
```