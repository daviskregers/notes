# Restarting stopped containers

```
docker run busybox echo hi there
```

```
davis@davis-arch  ~  docker ps --all
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
0f4205109dba        busybox                        "echo hi there"          49 seconds ago      Exited (0) 48 seconds ago                                 eloquent_hawking
```

```
davis@davis-arch  ~  docker start -a 0f4205109dba
hi there
```

When created a container, we cannot replace the default command - for the `0f4205109dba` it will always be `echo hi there`.