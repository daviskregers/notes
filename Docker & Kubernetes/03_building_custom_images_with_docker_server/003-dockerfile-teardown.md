# Dockerfile teardown

Every line on the dockerfile instructs docker server what to do.

- `FROM` instructions the server to use a base image like `alpine`.
- `RUN` instructions the server to execute a command in the base image.
- `CMD` instructions the server to the command that is used when the container is started up.

More commands are available at [https://docs.docker.com/engine/reference/builder/#from](https://docs.docker.com/engine/reference/builder/#from)

