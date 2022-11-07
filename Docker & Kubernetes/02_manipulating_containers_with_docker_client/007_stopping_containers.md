# Stopping containers

You can use either `docker stop` or `docker kill` command to stop a container.

- When using `docker stop` you will issue a `SIGTERM` message to the process. It gives the process a little bit of time to shut down and do cleanup. 
- The `docker kill` issues `SIGKILL` message, which kills the process immediately.

If the `docker stop` does not stop within 10 seconds - it issues the kill command.

```
davis@davis-arch  ~  docker create busybox ping google.com
2fa3cb41f84d8576b634451c288b1ae4462d98314aa832275633139b94efe284
 davis@davis-arch  ~  docker start 2fa3cb41f84d8576b634451c288b1ae4462d98314aa832275633139b94efe284
2fa3cb41f84d8576b634451c288b1ae4462d98314aa832275633139b94efe284
 davis@davis-arch  ~  docker logs 2fa3cb41f84d8576b634451c288b1ae4462d98314aa832275633139b94efe284
PING google.com (64.233.162.101): 56 data bytes
64 bytes from 64.233.162.101: seq=0 ttl=46 time=23.328 ms
64 bytes from 64.233.162.101: seq=1 ttl=46 time=23.068 ms
64 bytes from 64.233.162.101: seq=2 ttl=46 time=23.231 ms
64 bytes from 64.233.162.101: seq=3 ttl=46 time=23.133 ms
64 bytes from 64.233.162.101: seq=4 ttl=46 time=23.241 ms
64 bytes from 64.233.162.101: seq=5 ttl=46 time=23.158 ms
64 bytes from 64.233.162.101: seq=6 ttl=46 time=23.231 ms
64 bytes from 64.233.162.101: seq=7 ttl=46 time=23.132 ms
64 bytes from 64.233.162.101: seq=8 ttl=46 time=23.010 ms
64 bytes from 64.233.162.101: seq=9 ttl=46 time=23.221 ms
64 bytes from 64.233.162.101: seq=10 ttl=46 time=23.220 ms
64 bytes from 64.233.162.101: seq=11 ttl=46 time=23.112 ms
64 bytes from 64.233.162.101: seq=12 ttl=46 time=24.198 ms
 davis@davis-arch  ~  docker ps
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
2fa3cb41f84d        busybox                        "ping google.com"        28 seconds ago      Up 20 seconds                                             xenodochial_wiles
 davis@davis-arch  ~  docker stop 2fa3cb41f84d
2fa3cb41f84d
davis@davis-arch  ~  docker start 2fa3cb41f84d
2fa3cb41f84d
 davis@davis-arch  ~  docker ps               
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
2fa3cb41f84d        busybox                        "ping google.com"        5 minutes ago       Up 7 seconds                                              xenodochial_wiles
 davis@davis-arch  ~  docker kill 2fa3cb41f84d
2fa3cb41f84d
```