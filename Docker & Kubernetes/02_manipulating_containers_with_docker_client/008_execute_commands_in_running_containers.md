# Execute commands in running containers

We can execute an additional command in a container using the

```
docker exec -it <container id> <command>
```

The `-it` flags allows us to provide input to the container, it connects the `STDIN`, `STDOUT` and `STDERR` channels between your terminal and the running process.
The `-i` flag connects the channels, the `-t` basically formats the output so it is prettier.


```
 davis@davis-arch  ~  docker create redis
5e993caa8ff4debe7e0bf6879546c76a8e21b372b560b8f348158c0b1c98ca86
 davis@davis-arch  ~  docker start 5e993caa8ff4debe7e0bf6879546c76a8e21b372b560b8f348158c0b1c98ca86
5e993caa8ff4debe7e0bf6879546c76a8e21b372b560b8f348158c0b1c98ca86
 davis@davis-arch  ~  docker ps
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
5e993caa8ff4        redis                          "docker-entrypoint.s…"   8 seconds ago       Up 1 second                     6379/tcp                  relaxed_williamson
 davis@davis-arch  ~  docker exec -it 5e993caa8ff4debe7e0bf6879546c76a8e21b372b560b8f348158c0b1c98ca86 redis-cli
127.0.0.1:6379> set myvalue 5
OK
127.0.0.1:6379> get myvalue
"5"
```

When using the `exec` without the `-it` it will just execute the `redis-cli` command and we will not be able to interact with it.

You can also use the `exec` command to get full terminal access of the container for debugging:

```
davis@davis-arch  ~  docker exec -it 5e993caa8ff4debe7e0bf6879546c76a8e21b372b560b8f348158c0b1c98ca86 bash
root@5e993caa8ff4:/data# ls /
bin  boot  data  dev  etc  home  lib  lib64  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
root@5e993caa8ff4:/data# hostname
5e993caa8ff4
```

You can also create the image at the start to use the terminal:

```
davis@davis-arch  ~  docker run -it busybox sh  
/ # ls /
bin   dev   etc   home  proc  root  sys   tmp   usr   var
/ # hostname
946745b94a5e
```