# Dockerizing React app

We'll dockerize the react app that we created in previous section.

```
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  touch client/Dockerfile.dev
```

```Dockerfile
FROM node:alpine
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "start"]
```

```
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  cd client 
 davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application/client   master  docker build -f Dockerfile.dev .
Sending build context to Docker daemon  233.9MB
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR '/app'
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY ./package.json ./
 ---> 89997607ce86
Step 4/6 : RUN npm install
 ---> Running in 61f78a9feb95
npm WARN deprecated kleur@2.0.2: Please upgrade to kleur@3 or migrate to 'ansi-colors' if you prefer the old syntax. Visit <https://github.com/lukeed/kleur/releases/tag/v3.0.0\> for migration path(s).
npm WARN deprecated circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.

npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN ts-pnp@1.0.0 requires a peer of typescript@* but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.7 (node_modules/chokidar/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.7: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1853 packages from 729 contributors and audited 36407 packages in 222.036s
found 63 low severity vulnerabilities
  run `npm audit fix` to fix them, or `npm audit` for details
Removing intermediate container 61f78a9feb95
 ---> c323bbd27a3d
Step 5/6 : COPY . .
 ---> d8a0e0b9092f
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in 6a35d272baca
Removing intermediate container 6a35d272baca
 ---> 0cfda483865f
Successfully built 0cfda483865f
```
