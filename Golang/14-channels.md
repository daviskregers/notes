# Channels

- Channel basics
    - create a channel with make command
        - make(chan int)
    - send a message into channel
        - ch <- val
    - receive from channel
        - val := <-ch
    - Can have multiple senders and receivers
- Restricting data flow
    - Channel can be cast into send-only or receive-only versions
        - send-only: chan <- int
        - receive only: <-chan int
- Buffered channels
    - Channels block sender side till receiver is available
    - Block receiver side till message is available
    - Can decouple sender and receiver with buffered channels
        - make(chan int, 50)
    - Use buffered channels when sender and receiver have assymmetric loads
- For..range loops with channels
    - Use to monitor channel and process messages as they arrive
    - Loop exits when channel is closed
- Select statements
    - Allows goroutine to monitor several channels at once
        - Blocks if all channels block
        - If multiple channels receive value simultaneously, behaviour is undefined

```go
package main          
                                                      
import (              
        "fmt"                                         
        "sync"                                                                                              
        "time"                               
)                
                                                      
var wg = sync.WaitGroup{}                    
                                                      
var logCh = make(chan logEntry, 50)          
var doneCh = make(chan struct{}) // signal only channel                                   
                      
func main() {         
    ch := make(chan int)    
                                             
    // Bidirectional comms                                                                                                 
    wg.Add(2)    
    go func() {
        i := <- ch    
        fmt.Println(i) // 42
        ch <- 27                             
        wg.Done()                                                                         
    }()                                      
    go func() {       
        i := 42                              
        ch <- i       
        fmt.Println(<-ch)                    
        wg.Done()                            
    }()                                      
    wg.Wait()        
                                             
    // 1 send, 1 read thread                                                                                
                                             
    wg.Add(2)                                
                                             
    go func(ch <-chan int) {                          
        i := <- ch
        fmt.Println(i)                                                                                      
        // ch <- 27 -- cannot send, receive only                                                                                       
        wg.Done()
    }(ch)                                    
                      
    go func(ch chan<- int) {                          
        ch <- 42      
        // fmt.Println(<-ch) -- cannot receive, send only                                                                              
        wg.Done()
    }(ch)                                                                                 
    wg.Wait()                                                                             
                                             
    // multiple messages                              
                                             
    ch2 := make(chan int, 50)                                      
    wg.Add(2)                                                                             
    go func(ch <- chan int) {                                                             
        for {                                
            if i, ok := <- ch; ok {          
                fmt.Println(i)
            } else {
                break      
            }   
        }           
        wg.Done()                            
    }(ch2)                                   
    go func(ch chan<- int) {                                       
        ch <- 42                 
        ch <- 27           
        ch <- 13                 
        close(ch)          
        wg.Done()                                                                                           
    }(ch2)                                                                                                  
    wg.Wait()                                         

    // logger                                         
                           
    go logger()                  
    logCh <- logEntry{time.Now(), logInfo, "App is starting"}                                                                          
    logCh <- logEntry{time.Now(), logInfo, "App is shutting down"}                                                                     
    time.Sleep(100 * time.Millisecond)                
                                                      
    doneCh <- struct{}{}                                           
}                                

const (                          
    logInfo = "INFO"             
    logWarning = "WARNING"                                         
    logError = "ERROR"                                             
)                                

type logEntry struct {                                             
    time time.Time               
    severity string              
    message string               
}                                

func logger() {                  
    for {                        
        select {                 
        case entry := <- logCh:                                    
            fmt.Printf("%v - [%v] %v\n", entry.time.Format("2006-01-02T15:04:05"), entry.severity, entry.message)
        case <-doneCh:                                             
            break                
        }                        
    }                            
}                                
```

```go
42
27
42
42
27
13
2019-12-25T16:20:09 - [INFO] App is starting
2019-12-25T16:20:09 - [INFO] App is shutting down
```