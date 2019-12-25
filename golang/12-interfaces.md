# Interfaces

- Basics 
    ```go
    type Writer interface {
        Write([]byte) (int, error)
    }

    type ConsoleWriter struct {}

    func (cw ConsoleWriter) Write(data []byte) (int, error) {
        n, err := fmt.Println(string(data))
        return n, err
    }
    ```
- Composing interfaces
    ```go
    type Writer interface {
        Write([]byte) (int, error)
    }
    type Closer interface {
        Close() error
    }
    type WriterCloser interface {
        Writer
        Closer
    }
    ```
- Type conversion
    ```go
    var wc WriterCloser = NewBufferedWriterCloser()
    bwc := wc.(*BufferedWriterCloser)
    ```
    - The empty interface and type switches
    ```go
    var i interface{} = 0
    switch i.(type) {
        case int: ...
        case string: ...
        default: ...
    }
    ```
- Implementing with values vs pointers
    - Method set of a `value` is all methods with value receivers
    - Method set of a `pointer` is all methods, regardless of receiver type
- Best Practices
    - Use many, small interfaces vs large monolythic ones
        - io.Writer, io.Reader, interface{}
    - Don't export interfaces for types that will be consumed
    - Do export interfaces for types that will be used by package
    - Design functions and methods to receive interfaces whenever possible


```go
package main

import (
        "bytes"
        "fmt"
)

func main() {
    var w Writer = ConsoleWriter{}
    w.Write([]byte("Hello Go!"))

    myInt := IntCounter(0)
    var inc Incrementer = &myInt
    for i := 0; i < 10; i++ {
        fmt.Println(inc.Inrement())
    }

    var wc WriterCloser = NewBufferedWriterCloser()
    wc.Write([]byte("Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer efficitur consequat facilisis. Sed iaculis metus."))
    wc.Close()
}


type Writer interface {
    Write([]byte) (int, error)
}

type ConsoleWriter struct {}

func (cw ConsoleWriter) Write(data []byte) (int, error) {
    n, err := fmt.Println(string(data))
    return n, err
}

//

type Incrementer interface {
    Inrement() int
}

type IntCounter int

func (ic *IntCounter) Inrement() int {
    *ic++
    return int(*ic)
}

//

type Closer interface {
    Close() error
}

type WriterCloser interface {
    Writer
    Closer
}

type BufferedWriterCloser struct {
    buffer *bytes.Buffer
}

func (bwc *BufferedWriterCloser) Write(data[]byte) (int, error) {
    n, err := bwc.buffer.Write(data)
    if err != nil {
        return 0, err
    }
    v := make([]byte, 8)
    for bwc.buffer.Len() > 8 {
        _, err := bwc.buffer.Read(v)
        if err != nil {
            return 0, err
        }
        _, err = fmt.Println(string(v))
        if err != nil {
            return 0, err
        }
    }

    return n, nil
}

func (bwc *BufferedWriterCloser) Close() error {
    for bwc.buffer.Len() > 0 {
        data := bwc.buffer.Next(8)
        _, err := fmt.Println(string(data))
        if err != nil {
            return err
        }
    }
    return nil
}

func NewBufferedWriterCloser() *BufferedWriterCloser {
    return &BufferedWriterCloser{
        buffer: bytes.NewBuffer([]byte{}),
    }
}
```

```go
Hello Go!
1
2
3
4
5
6
7
8
9
10
Lorem ip
sum dolo
r sit am
et, cons
ectetur 
adipisci
ng elit.
 Integer
 efficit
ur conse
quat fac
ilisis. 
Sed iacu
lis metu
s.
```