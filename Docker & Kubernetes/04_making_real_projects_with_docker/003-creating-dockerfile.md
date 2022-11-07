# Creating a dockerfile & few planned errors

When using the node server, we need to run two commands `npm install` to install the dependencies and `npm start` to start the application.

So, when creating a dockerfile, we'll need to:
1. Specify a base image
2. Run some commands to install dependencies
3. Specify a command to run on starup

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  touch Dockerfile
```

```Dockerfile
# Specify a base image
FROM alpine

# Install dependencies
RUN npm install

# Default command
CMD ["npm", "start"]
```

When trying to build the image:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker build .
Sending build context to Docker daemon  4.096kB
Step 1/3 : FROM alpine
 ---> caf27325b298
Step 2/3 : RUN npm install
 ---> Running in 262e1fdf7e56
/bin/sh: npm: not found
The command '/bin/sh -c npm install' returned a non-zero code: 127
```

This throws an error that we do not have the `npm` program.

We can fix this in 2 ways - find a different base image that has `npm` installed or write some extra steps to install it.
We'll use a different image, we can find those at [https://hub.docker.com](https://hub.docker.com).

```Dockerfile
# Specify a base image
FROM node:alpine

# Install dependencies
RUN npm install

# Default command
CMD ["npm", "start"]
```

Now we can build it:

```
 ✘ davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker build .
Sending build context to Docker daemon  4.096kB
Step 1/3 : FROM node:alpine
alpine: Pulling from library/node
169185f82c45: Pull complete 
80e1b3e484f0: Pull complete 
93e33f1be740: Pull complete 
Digest: sha256:2558617051e2c402a1bc6df5a73838e3e2832efff356ff38b9ffaa1ce562f9cb
Status: Downloaded newer image for node:alpine
 ---> ebbf98230a82
Step 2/3 : RUN npm install
 ---> Running in 95f311d239ab
npm WARN saveError ENOENT: no such file or directory, open '/package.json'
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN enoent ENOENT: no such file or directory, open '/package.json'
npm WARN !invalid#2 No description
npm WARN !invalid#2 No repository field.
npm WARN !invalid#2 No README data
npm WARN !invalid#2 No license field.

up to date in 0.614s
found 0 vulnerabilities

Removing intermediate container 95f311d239ab
 ---> 0ade00c69ba0
Step 3/3 : CMD ["npm", "start"]
 ---> Running in 09e408a91110
Removing intermediate container 09e408a91110
 ---> 7beb9507123a
Successfully built 7beb9507123a
```

Now we can see that we are missing the `package.json` file, this can be fixed by using the `COPY <local path> <remote path>`  instruction:
Note that the local path is relative to local build context.

```Dockerfile
# Specify a base image
FROM node:alpine

# Install dependencies
COPY ./ ./
RUN npm install

# Default command
CMD ["npm", "start"]
```

Now we can successfully build it:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker build .
Sending build context to Docker daemon  4.096kB
Step 1/4 : FROM node:alpine
 ---> ebbf98230a82
Step 2/4 : COPY ./ ./
 ---> 0babb3e5ff58
Step 3/4 : RUN npm install
 ---> Running in 6969bdd45b86
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN !invalid#2 No description
npm WARN !invalid#2 No repository field.
npm WARN !invalid#2 No license field.

added 48 packages from 36 contributors and audited 121 packages in 5.019s
found 0 vulnerabilities

Removing intermediate container 6969bdd45b86
 ---> 0421b41270aa
Step 4/4 : CMD ["npm", "start"]
 ---> Running in dec101331c5c
Removing intermediate container dec101331c5c
 ---> 7c639816f391
Successfully built 7c639816f391
```

Tag it:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master ●  docker build -t daviskregers/simpleweb .
Sending build context to Docker daemon  4.096kB
Step 1/4 : FROM node:alpine
 ---> ebbf98230a82
Step 2/4 : COPY ./ ./
 ---> Using cache
 ---> 0babb3e5ff58
Step 3/4 : RUN npm install
 ---> Using cache
 ---> 0421b41270aa
Step 4/4 : CMD ["npm", "start"]
 ---> Using cache
 ---> 7c639816f391
Successfully built 7c639816f391
Successfully tagged daviskregers/simpleweb:latest
```

And run it:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master ●  docker run daviskregers/simpleweb

> @ start /
> node index.js

Listening on port 8080
```

Now the app is running in the container, but we havent specified that we allow network access to it, so we cannot open the port 8080 and view it in our browser.
We can fix it specifying port mapping.

```
docker run -p <outer port>:<port inside container> <image>
```

```
✘ davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker run -p 8080:8080 daviskregers/simpleweb

> @ start /
> node index.js

Listening on port 8080

```

Now we can access it:

![](../../images/2019-02-01-12-31-24.png)