# Creating docker images

Previously we have made use of docker images that are already built by someone.  We can create our own docker images by creating a Dockerfile that defines the configuration of the container, then we build it using by docker client, the docker server builds it into a usable image.

The Dockerfile creation flow looks something like this:
1. Specify a base image
2. Run some commands to install additional programs
3. Specify a command to run on container startup

