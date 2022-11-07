# Duplicating dependencies

If you notice in the last section when we ran the build process, there was a line:

```
 ✘ davis@davis-arch  ~/projects/docker/04_react_app   master  docker build -f Dockerfile.dev .
Sending build context to Docker daemon    244MB
```

This is thrown because we have a duplicate dependencies folder - we have a copy on our local machine and then the docker is installing them.
The easiest way to solve this problem is simply by deleting the `node_modules` directory on our local machine.

```
davis@davis-arch  ~/projects/docker/04_react_app   master  rm -r node_modules 
 davis@davis-arch  ~/projects/docker/04_react_app   master  docker build -f Dockerfile.dev .
Sending build context to Docker daemon  715.3kB
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> Using cache
 ---> a33dd4926364
Step 4/6 : RUN npm install
 ---> Using cache
 ---> 2f4e0c88fbee
Step 5/6 : COPY . .
 ---> 297ad62ace07
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in 92f50d91be7e
Removing intermediate container 92f50d91be7e
 ---> 3b1edaee87fb
Successfully built 3b1edaee87fb
```

Now the build process is much faster.