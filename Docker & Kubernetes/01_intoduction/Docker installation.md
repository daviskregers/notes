# OSX

1. Sign up for a [[Docker Hub]] account [https://hub.docker.com/editions/community/docker-ce-desktop-mac]
2. Download / Install [[Docker for Mac]] 
3. Login to [[Docker]]
4. Verify docker installation

```
docker version
```

# Windows

If you are a Windows Home user, you will not be able install the [[Docker for Windows]] Desktop edition, as it requires [[Hyper-V virtualization]]. This is supported only by [[Windows Professional]] and Enterprise editions.

[[Windows Home]] users will need to install [[Docker Toolbox]] which uses [[VirtualBox]] instead. Please follow the instructions below for installation:

https://docs.docker.com/toolbox/toolbox_install_windows/

You may also need to enable virtualisation in your computer's [[BIOS settings]]. This will be different for each manufacturer, please refer to their documentation on which keys to use to access these settings on reboot.

*Note*

A major difference between the course lecture using [[Docker Desktop]] vs. [[Docker Toolbox]] is that you will not be able to use [[localhost]] anymore.

Instead, you will need to access your machine with the [[IP Address]] 192.168.99.100

1. Sign up for a Docker Hub account [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
2. Download / Install [[Docker for Windows]]
3. Login with [[Docker]]
4. Verify docker installation

# Linux

https://docs.docker.com/install/linux/docker-ce/ubuntu/#set-up-the-repository