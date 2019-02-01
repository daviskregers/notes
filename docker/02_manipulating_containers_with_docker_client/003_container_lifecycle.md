# Container lifecycle

When using a `docker run` command we actually execute two separate commands - `docker create` and `docker start` where we first create a container and then start it.

```
docker create <image-name>
docker start <container-id>
```

When creating a container, we take the the filesystem snapshot from the image and prepare it for using in the docker virtual machine. When starting the container, we execute the startup commands that comes with the image.

```
davis@davis-arch  ~  docker create hello-world
ab1242a52208c5b4185239e697bb160db7d37f1101ae62d6975899cbb66a5e1b
 davis@davis-arch  ~  docker start -a ab1242a52208c5b4185239e697bb160db7d37f1101ae62d6975899cbb66a5e1b

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

 davis@davis-arch  ~  
```

The `-a` flag stands for watching the output and printing it out on the terminal.

Without it we get:

```
davis@davis-arch  ~  docker start ab1242a52208c5b4185239e697bb160db7d37f1101ae62d6975899cbb66a5e1b 
ab1242a52208c5b4185239e697bb160db7d37f1101ae62d6975899cbb66a5e1b
```

