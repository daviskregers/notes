# Shorthand with docker compose

The previous approach is working well, but the command can get ridiculously long and that can be a pain.
We can make a `docker-compose.yml` to simplify the command we have to run.

```
 davis@davis-arch  ~/projects/docker/04_react_app   master  touch docker-compose.yml
```

```yaml
version: '3'
services:
  web:
    build: 
      context: .
      dockerfile: Dockerfile.dev
    ports:
      - "3000:3000"
    volumes:
      - /app/node_modules
      - .:/app
```

Now we can use:

```
davis@davis-arch  ~/projects/docker/04_react_app   master  docker-compose up
Creating network "04_react_app_default" with the default driver
Building web
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> c1b398fa1193
Step 4/6 : RUN npm install
 ---> Running in b75a8612d065
npm WARN deprecated kleur@2.0.2: Please upgrade to kleur@3 or migrate to 'ansi-colors' if you prefer the old syntax. Visit <https://github.com/lukeed/kleur/releases/tag/v3.0.0\> for migration path(s).
npm WARN deprecated circular-json@0.3.3: CircularJSON is in maintenance only, flatted is its successor.
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1949 packages from 671 contributors and audited 35817 packages in 39.824s
found 0 vulnerabilities

Removing intermediate container b75a8612d065
 ---> f1a451e57b5f
Step 5/6 : COPY . .
 ---> 706a952c1afc
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in 4284cd9f9286
Removing intermediate container 4284cd9f9286
 ---> 092bf95af1b7
Successfully built 092bf95af1b7
Successfully tagged 04_react_app_web:latest
WARNING: Image for service web was built because it did not already exist. To rebuild this image you must use `docker-compose build` or `docker-compose up --build`.
Creating 04_react_app_web_1 ... done
Attaching to 04_react_app_web_1
web_1  | 
web_1  | > frontend@0.1.0 start /app
web_1  | > react-scripts start
web_1  | 
web_1  | Starting the development server...
web_1  | 
web_1  | Compiled successfully!
web_1  | 
web_1  | You can now view frontend in the browser.
web_1  | 
web_1  |   Local:            http://localhost:3000/
web_1  |   On Your Network:  http://172.21.0.2:3000/
web_1  | 
web_1  | Note that the development build is not optimized.
web_1  | To create a production build, use npm run build.
web_1  | 
```

And the app will work in the browser like before.