# Setting up dockerfile

```
davis@davis-arch  ~/projects/docker/03_visits   master  touch Dockerfile
```

```Dockerfile
FROM node:alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
```

```
 davis@davis-arch  ~/projects/docker/03_visits   master  docker build .
Sending build context to Docker daemon  4.096kB
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Running in d4519a0af637
Removing intermediate container d4519a0af637
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> 320ca3885ebb
Step 4/6 : RUN npm install
 ---> Running in 891c0beb8c1c
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN app No description
npm WARN app No repository field.
npm WARN app No license field.

added 52 packages from 40 contributors and audited 125 packages in 2.091s
found 0 vulnerabilities

Removing intermediate container 891c0beb8c1c
 ---> 0841db5e3d2d
Step 5/6 : COPY . .
 ---> 340dc4bf7dd5
Step 6/6 : CMD ['npm', 'start']
 ---> Running in 3f37edffadb0
Removing intermediate container 3f37edffadb0
 ---> 535452064704
Successfully built 535452064704
 davis@davis-arch  ~/projects/docker/03_visits   master  docker build -t daviskregers/visits:latest .
Sending build context to Docker daemon  4.096kB
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> Using cache
 ---> 320ca3885ebb
Step 4/6 : RUN npm install
 ---> Using cache
 ---> 0841db5e3d2d
Step 5/6 : COPY . .
 ---> Using cache
 ---> 340dc4bf7dd5
Step 6/6 : CMD ['npm', 'start']
 ---> Using cache
 ---> 535452064704
Successfully built 535452064704
Successfully tagged daviskregers/visits:latest
```