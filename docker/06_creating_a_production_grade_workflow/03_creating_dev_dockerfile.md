# Creating Dev Dockerfile

Most likely it will make more sense to create 2 separate dockerfiles - one for development and one for production.

```
davis@davis-arch  ~/projects/docker   master  touch Dockerfile.dev
```

```Dockerfile
FROM node:alpine
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```

Note, that since the filename is changed, we'll need to use `-f` flag to specify it:

```
davis@davis-arch  ~/projects/docker/04_react_app   master  docker build .      
unable to prepare context: unable to evaluate symlinks in Dockerfile path: lstat /home/davis/projects/docker/04_react_app/Dockerfile: no such file or directory
 ✘ davis@davis-arch  ~/projects/docker/04_react_app   master  docker build -f Dockerfile.dev .
Sending build context to Docker daemon    244MB
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> a33dd4926364
Step 4/6 : RUN npm install
 ---> Running in 0f7cda2e8098
npm WARN deprecated circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.
npm WARN deprecated kleur@2.0.2: Please upgrade to kleur@3 or migrate to 'ansi-colors' if you prefer the old syntax. Visit <https://github.com/lukeed/kleur/releases/tag/v3.0.0\> for migration path(s).
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1949 packages from 671 contributors and audited 35817 packages in 43.316s
found 0 vulnerabilities

Removing intermediate container 0f7cda2e8098
 ---> 2f4e0c88fbee
Step 5/6 : COPY . .
 ---> 64ba876f1a5c
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in a50100fb5243
Removing intermediate container a50100fb5243
 ---> 4a42cf02f626
Successfully built 4a42cf02f626
```
