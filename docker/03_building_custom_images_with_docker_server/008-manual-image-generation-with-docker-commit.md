# Manual Image Generation with Docker commit

When looking at the build process, we can see that we can create a container, execute commands in it and generate an image from that container.

We can start up an empty `alpine` image:

```
/ # apk add --update redis
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/main/x86_64/APKINDEX.tar.gz
fetch http://dl-cdn.alpinelinux.org/alpine/v3.9/community/x86_64/APKINDEX.tar.gz
(1/1) Installing redis (4.0.12-r0)
Executing redis-4.0.12-r0.pre-install
Executing redis-4.0.12-r0.post-install
Executing busybox-1.29.3-r10.trigger
OK: 7 MiB in 15 packages
/ # 
```

Now, while that is running, in a second terminal we can execute:

```
davis@davis-arch  ~  docker ps
CONTAINER ID        IMAGE                          COMMAND                  CREATED             STATUS                          PORTS                     NAMES
cd1e9a4372d7        alpine                         "sh"                     48 seconds ago      Up 46 seconds                                             keen_swirles
 davis@davis-arch  ~  docker commit -c 'CMD ["redis-server"]' cd1e9a4372d7
sha256:e1380e3df76f340d8f848942547a0d7f9e11f8843bef80d8de9df84dd186084d
```

Now we can run it:

```
davis@davis-arch  ~  docker run e1380e3df76f340d8f84894
1:C 01 Feb 09:54:36.233 # oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
1:C 01 Feb 09:54:36.233 # Redis version=4.0.12, bits=64, commit=1be97168, modified=0, pid=1, just started
1:C 01 Feb 09:54:36.233 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
1:M 01 Feb 09:54:36.234 * Running mode=standalone, port=6379.
1:M 01 Feb 09:54:36.234 # WARNING: The TCP backlog setting of 511 cannot be enforced because /proc/sys/net/core/somaxconn is set to the lower value of 128.
1:M 01 Feb 09:54:36.234 # Server initialized
1:M 01 Feb 09:54:36.234 # WARNING overcommit_memory is set to 0! Background save may fail under low memory condition. To fix this issue add 'vm.overcommit_memory = 1' to /etc/sysctl.conf and then reboot or run the command 'sysctl vm.overcommit_memory=1' for this to take effect.
1:M 01 Feb 09:54:36.235 # WARNING you have Transparent Huge Pages (THP) support enabled in your kernel. This will create latency and memory usage issues with Redis. To fix this issue run the command 'echo never > /sys/kernel/mm/transparent_hugepage/enabled' as root, and add it to your /etc/rc.local in order to retain the setting after a reboot. Redis must be restarted after THP is disabled.
1:M 01 Feb 09:54:36.235 * Ready to accept connections
```
