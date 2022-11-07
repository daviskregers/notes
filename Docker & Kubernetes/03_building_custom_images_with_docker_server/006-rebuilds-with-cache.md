# Rebuilds with cache

When building we have a filesystem snapshot of every step in the build process. 
If we modify the previously build Dockerfile to install `gcc`:

```
# Use an existing docker image as a base
FROM alpine

# Download and install all dependencies
RUN  apk add --update redis
RUN  apk add --update gcc

# Tell the image what to do when it starts as a container
CMD ["redis-server"]
```

And run the

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

You can see that the 1st and the 2nd step is not  executed - docker realised that nothing has changed in these steps and it can use previously created file system snapshots. When it sees that there is a new instruction to be executed, from that point on it executes the actual building steps.