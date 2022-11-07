# Specifying working directory

When running:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker run daviskregers/simpleweb sh
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  docker run -it daviskregers/simpleweb sh
/ # ls
Dockerfile         lib                package.json       sys
bin                media              proc               tmp
dev                mnt                root               usr
etc                node_modules       run                var
home               opt                sbin
index.js           package-lock.json  srv
```

You can notice that we copied all the files to the root directory of the system, which is not a good practice.
We can use working directory instruction to fix this:

```Dockerfile
# Specify a base image
FROM node:alpine
WORKDIR /usr/app

# Install dependencies
COPY ./ ./
RUN npm install

# Default command
CMD ["npm", "start"]
```

All the instructions after the `WORKDIR` instruction, will be executed relative to the location provided.

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master ●  docker build -t daviskregers/simpleweb .      
Sending build context to Docker daemon  4.096kB
Step 1/5 : FROM node:alpine
 ---> ebbf98230a82
Step 2/5 : WORKDIR /usr/app
 ---> Running in 78a45d7af5f5
Removing intermediate container 78a45d7af5f5
 ---> 81d0968ef0fb
Step 3/5 : COPY ./ ./
 ---> 50acb7b5ba76
Step 4/5 : RUN npm install
 ---> Running in 07c874380805
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN app No description
npm WARN app No repository field.
npm WARN app No license field.

added 48 packages from 36 contributors and audited 121 packages in 2.2s
found 0 vulnerabilities

Removing intermediate container 07c874380805
 ---> 69eec757ea8c
Step 5/5 : CMD ["npm", "start"]
 ---> Running in 882e18a3c487
Removing intermediate container 882e18a3c487
 ---> 11a6a82ed208
Successfully built 11a6a82ed208
Successfully tagged daviskregers/simpleweb:latest
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master ●  docker run -it daviskregers/simpleweb sh
/usr/app # ls
Dockerfile         node_modules       package.json
index.js           package-lock.json
/usr/app # pwd
/usr/app
```