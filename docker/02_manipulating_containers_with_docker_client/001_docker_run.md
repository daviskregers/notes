# Docker run in detail

`docker run` is a command for creating and running a container from an image. 

```
docker run <image name>
```

```
docker run hello-world
```

It gets an image that it is supposed to create a container from, puts it onto the linux virtual machine and runns the process. Image contains file system snapshot that is put onto the virtual machine's disk space, then it executes the images startup commands to launch the process.

We can override startup command using:

```
docker run <image-name> command
```

```
docker run busybox echo hi there
```

```
davis@davis-arch  ~  docker run busybox echo hi there
Unable to find image 'busybox:latest' locally
latest: Pulling from library/busybox
57c14dd66db0: Pull complete 
Digest: sha256:7964ad52e396a6e045c39b5a44438424ac52e12e4d5a25d94895f2058cb863a0
Status: Downloaded newer image for busybox:latest
hi there
```

```
davis@davis-arch  ~  docker run busybox ls           
bin
dev
etc
home
proc
root
sys
tmp
usr
var
```

