# Building a dockerfile

To build an image that runs a redis-server, we can create a new directory for our project

```
davis@davis-arch  ~/projects/docker   master  mkdir 01_redis-image
davis@davis-arch  ~/projects/docker   master  cd 01_redis-image 
davis@davis-arch  ~/projects/docker   master  code .
```

And create a new `Dockerfile` with following content:

```
# Use an existing docker image as a base
FROM alpine

# Download and install all dependencies
RUN  apk add --update redis

# Tell the image what to do when it starts as a container
CMD ["redis-server"]
```



Now we can build the image:

```
davis@davis-arch  ~/projects/docker   master  cd 01_redis-image 
davis@davis-arch  ~/projects/docker/01_redis-image   master  docker build .
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM alpine
latest: Pulling from library/alpine
6c40cc604d8e: Pull complete 
Digest: sha256:b3dbf31b77fd99d9c08f780ce6f5282aba076d70a513a8be859d8d3a4d0c92b8
Status: Downloaded newer image for alpine:latest
 ---> caf27325b298
Step 2/3 : RUN  apk add --update redis
 ---> Running in db036af84433
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/community/x86_64/APKINDEX.tar.gz
(1/1) Installing redis (4.0.12-r0)
Executing redis-4.0.12-r0.pre-install
Executing redis-4.0.12-r0.post-install
Executing busybox-1.29.3-r10.trigger
OK: 7 MiB in 15 packages
Removing intermediate container db036af84433
 ---> 6af5b67c4479
Step 3/3 : CMD ["redis-server"]
 ---> Running in 30207662f6e4
Removing intermediate container 30207662f6e4
 ---> f84d58cd025b
Successfully built f84d58cd025b
```

Now we can run it:

```
davis@davis-arch  ~/projects/docker/01_redis-image   master  docker run f84d58cd025b
1:C 01 Feb 08:59:01.892 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 01 Feb 08:59:01.892 # Redis version=4.0.12, bits=64, commit=1be97168, modified=0, pid=1, just started
1:C 01 Feb 08:59:01.892 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 01 Feb 08:59:01.894 * Running mode=standalone, port=6379.
1:M 01 Feb 08:59:01.894 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 01 Feb 08:59:01.894 # Server initialized
1:M 01 Feb 08:59:01.894 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 01 Feb 08:59:01.894 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 01 Feb 08:59:01.894 * Ready to accept connections
```
