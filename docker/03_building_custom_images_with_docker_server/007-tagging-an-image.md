# Tagging an image

When we previously built the image:

```
davis@davis-arch  ~/projects/docker/01_redis-image    docker build .
Sending build context to Docker daemon  2.048kB
Step 1/4 : FROM alpine
 ---> caf27325b298
Step 2/4 : RUN  apk add --update redis
 ---> Using cache
 ---> 6af5b67c4479
Step 3/4 : RUN  apk add --update gcc
 ---> Running in 2c413c45fe6d
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/community/x86_64/APKINDEX.tar.gz
(1/10) Installing binutils (2.31.1-r2)
(2/10) Installing gmp (6.1.2-r1)
(3/10) Installing isl (0.18-r0)
(4/10) Installing libgomp (8.2.0-r2)
(5/10) Installing libatomic (8.2.0-r2)
(6/10) Installing libgcc (8.2.0-r2)
(7/10) Installing mpfr3 (3.1.5-r1)
(8/10) Installing mpc1 (1.0.3-r1)
(9/10) Installing libstdc++ (8.2.0-r2)
(10/10) Installing gcc (8.2.0-r2)
Executing busybox-1.29.3-r10.trigger
OK: 93 MiB in 25 packages
Removing intermediate container 2c413c45fe6d
 ---> 28c2cb2354aa
Step 4/4 : CMD ["redis-server"]
 ---> Running in 4fdc91f5f841
Removing intermediate container 4fdc91f5f841
 ---> 7874f97a4551
Successfully built 7874f97a4551
```

We get an image with an ID `7874f97a4551`, we can use tagging to give the image a more memorable name:

```
davis@davis-arch  ~/projects/docker/01_redis-image   master  docker build -t daviskregers/redis:latest .
Sending build context to Docker daemon  2.048kB
Step 1/4 : FROM alpine
 ---> caf27325b298
Step 2/4 : RUN  apk add --update redis
 ---> Using cache
 ---> 6af5b67c4479
Step 3/4 : RUN  apk add --update gcc
 ---> Using cache
 ---> 28c2cb2354aa
Step 4/4 : CMD ["redis-server"]
 ---> Using cache
 ---> 7874f97a4551
Successfully built 7874f97a4551
Successfully tagged daviskregers/redis:latest
```

The convention for tagging - `your_docker_id/project_name:version`.

Now we can start a container by using:

```
davis@davis-arch  ~/projects/docker/01_redis-image   master  docker run daviskregers/redis
1:C 01 Feb 09:48:03.415 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 01 Feb 09:48:03.415 # Redis version=4.0.12, bits=64, commit=1be97168, modified=0, pid=1, just started
1:C 01 Feb 09:48:03.415 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 01 Feb 09:48:03.417 * Running mode=standalone, port=6379.
1:M 01 Feb 09:48:03.417 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 01 Feb 09:48:03.417 # Server initialized
1:M 01 Feb 09:48:03.417 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 01 Feb 09:48:03.417 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 01 Feb 09:48:03.417 * Ready to accept connections
```