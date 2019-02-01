# What is a base image?

When writing a dockerfile, we'll always need an initial step of having an operating system where to execute all the additional steps of setting everything up.
When we specify using a base image, we do an initial step of setting up an operating system, all the programs we need in order to start working on our project.

In previous section we made use of `alpine` base image because it is a small linux operating system that includes a package manager program, that makes it very convenient to install additional software like redis.

You can use other base images like: `scratch`, `busybox`, `ubuntu`, `centos`