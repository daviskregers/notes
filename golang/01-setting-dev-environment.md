# Setting dev environment

You can download go language and it's tools at [https://golang.org/dl](https://golang.org/dl).

The installation instructions can be found at [https://golang.org/doc/install](https://golang.org/doc/install).

Since I'm on arch, I can run the following command.

```zsh
➜  learning git:(master) ✗ sudo pacman -S go go-tools
resolving dependencies...
looking for conflicting packages...

Packages (2) go-2:1.13.5-1  go-tools-2:1.13+3523+65e3620a7-3

Total Download Size:   140.22 MiB
Total Installed Size:  624.15 MiB

:: Proceed with installation? [Y/n] 
:: Retrieving packages...
 go-2:1.13.5-1-x86_64                                                                                              113.0 MiB  1082 KiB/s 01:47 [#######################################################################################] 100%
 go-tools-2:1.13+3523+65e3620a7-3-x86_64                                                                            27.2 MiB  1186 KiB/s 00:23 [#######################################################################################] 100%
(2/2) checking keys in keyring                                                                                                                 [#######################################################################################] 100%
(2/2) checking package integrity                                                                                                               [#######################################################################################] 100%
(2/2) loading package files                                                                                                                    [#######################################################################################] 100%
(2/2) checking for file conflicts                                                                                                              [#######################################################################################] 100%
(2/2) checking available disk space                                                                                                            [#######################################################################################] 100%
:: Processing package changes...
(1/2) installing go                                                                                                                            [#######################################################################################] 100%
(2/2) installing go-tools                                                                                                                      [#######################################################################################] 100%
:: Running post-transaction hooks...
(1/1) Arming ConditionNeedsUpdate...

```

## Test that it works

```zsh
➜  learning git:(master) ✗ go version
go version go1.13.5 linux/amd64
```

## Setting up paths

There are 2 environment variables that can be set up for golang.

```zsh
$GOROOT - indicates on where the golang is installed.
$GOPATH - indicates on where all the packages will go
            - You can specify multiple directories, it will search all of them.
            - When using `go get` that downloads packages, it will use the first directory.

If needed, you can modify them in your .basrc / .zshrc files.

```

I'm going to set up 2 paths - one for libraries, one for this learning project.

```zsh
export GOPATH=/home/davis/.golib:/home/davis/projects/learning/golang
```

## Structure

Within these paths you will see 3 main directories:

```zsh
bin     - compiled binaries
pkg     - when compiling, creates intermediate binaries so you don't have to recompile them every time
src     - source code
```

We are going to create these 3 directories in our `GOPATH`.

```zsh
➜  golang git:(master) ✗ pwd
/home/davis/projects/learning/golang
➜  golang git:(master) ✗ mkdir bin pkg src
➜  golang git:(master) ✗ ls
bin  pkg  src
```

## Hello world application

When creating a new application, we will create a new project in the `src` directory. The standard structure is to mirror the structure it would look like in source control. So it should look like this:

```zsh
➜  golang git:(master) ✗ mkdir -p src/github.com/daviskregers/helloworld     
➜  golang git:(master) ✗ tree
.
|-- bin
|-- pkg
`-- src
    `-- github.com
        `-- daviskregers
            `-- helloworld

```

In this `helloworld` directory we can add a new file `Main.go` with following contents.

```go
package main

import "fmt"

func main() {
        fmt.Println("Hello Go!")
}
```

Now there are multiple steps on how we can run the program.

- By running it:

```zsh
➜  golang git:(master) ✗ go run ./src/github.com/daviskregers/helloworld/Main.go
Hello Go!
```

- Building and running it

```zsh
➜  golang git:(master) ✗ go build ./src/github.com/daviskregers/helloworld
➜  golang git:(master) ✗ ./helloworld 
Hello Go!
```

- By installing it

```zsh
➜  golang git:(master) ✗ pwd
/home/davis/projects/learning/golang
➜  golang git:(master) ✗ ls bin 
➜  golang git:(master) ✗ go install github.com/daviskregers/helloworld
➜  golang git:(master) ✗ ls bin
helloworld
➜  golang git:(master) ✗ bin/helloworld 
Hello Go!
```