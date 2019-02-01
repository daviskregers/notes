# Build process in detail

Previously, when we ran the command

```
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

It gave our dockerfile to our cli. The `.` represents the `build context` that represents the files and folders that we want encapsulate in our container.

We had 3 steps in building an image:
1. Docker server checked our image cache and looked if we have ever downloaded an image called `alpine`, downloads it.
2. Docker server creates a container `db036af84433` of `alpine` where it runs the `apk add --update redis` command, takes the file system snapshot and removes the container.
3. Docker server creates a container `30207662f6e4` of previously created snapshot, sets up the primary command. Takes a snapshop and removes the container.

When all steps are done, we get the resulting snapshot, primary command and save it as an image as `f84d58cd025b`.

