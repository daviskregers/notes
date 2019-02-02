# Executing tests

On react executing tests are extremely straigh forward, basically all we have to do is to use the same Dockerfile and just change the last command to `npm run test`.

```
davis@davis-arch  ~/projects/docker/04_react_app   master  docker build -f Dockerfile.dev .
Sending build context to Docker daemon  716.8kB
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
 ---> 387cee59068b
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in 8a7360864aba
Removing intermediate container 8a7360864aba
 ---> 940d69d2b0af
Successfully built 940d69d2b0af
 davis@davis-arch  ~/projects/docker/04_react_app   master  docker run 940d69d2b0af npm run test

> frontend@0.1.0 test /app
> react-scripts test

PASS src/App.test.js
  ✓ renders without crashing (27ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.185s
Ran all test suites.
```

When running the command with `-it` flags, we get a fullscreen app with

```
PASS  src/App.test.js
  ✓ renders without crashing (23ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        1.197s
Ran all test suites.

Watch Usage
 › Press f to run only failed tests.
 › Press o to only run tests related to changed files.
 › Press q to quit watch mode.
 › Press t to filter by a test name regex pattern.
 › Press p to filter by a filename regex pattern.
 › Press Enter to trigger a test run.
```

But, if we make any changes, they will not reflect on the changes because we have no volumes mounted.
We'll modify the `docker-compose.yml` file for tests.

```Dockerfile
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
  tests:
    build:
      context: .
      dockerfile: Dockerfile.dev
    volumes:
      - /app/node_modules
      - .:/app
    command: ["npm", "run", "test"]
```

Now we can run 

```
davis@davis-arch  ~/projects/docker/04_react_app   master  docker-compose up --build
Building web
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> Using cache
 ---> c1b398fa1193
Step 4/6 : RUN npm install
 ---> Using cache
 ---> f1a451e57b5f
Step 5/6 : COPY . .
 ---> 8055397f2914
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Running in 3929c0160587
Removing intermediate container 3929c0160587
 ---> 8f8dc4a4edce
Successfully built 8f8dc4a4edce
Successfully tagged 04_react_app_web:latest
Building tests
Step 1/6 : FROM node:alpine
 ---> ebbf98230a82
Step 2/6 : WORKDIR /app
 ---> Using cache
 ---> 93b2648262c0
Step 3/6 : COPY package.json .
 ---> Using cache
 ---> c1b398fa1193
Step 4/6 : RUN npm install
 ---> Using cache
 ---> f1a451e57b5f
Step 5/6 : COPY . .
 ---> Using cache
 ---> 8055397f2914
Step 6/6 : CMD ["npm", "run", "start"]
 ---> Using cache
 ---> 8f8dc4a4edce
Successfully built 8f8dc4a4edce
Successfully tagged 04_react_app_tests:latest
Recreating 04_react_app_web_1 ... done
Creating 04_react_app_tests_1 ... done
Attaching to 04_react_app_web_1, 04_react_app_tests_1
web_1    | 
web_1    | > frontend@0.1.0 start /app
web_1    | > react-scripts start
web_1    | 
web_1    | Starting the development server...
web_1    | 
tests_1  | 
tests_1  | > frontend@0.1.0 test /app
tests_1  | > react-scripts test
tests_1  | 
web_1    | Compiled successfully!
web_1    | 
web_1    | You can now view frontend in the browser.
web_1    | 
web_1    |   Local:            http://localhost:3000/
web_1    |   On Your Network:  http://172.21.0.2:3000/
web_1    | 
web_1    | Note that the development build is not optimized.
web_1    | To create a production build, use npm run build.
web_1    | 
tests_1  | PASS src/App.test.js
tests_1  |   ✓ renders without crashing (24ms)
tests_1  | 
tests_1  | Test Suites: 1 passed, 1 total
tests_1  | Tests:       1 passed, 1 total
tests_1  | Snapshots:   0 total
tests_1  | Time:        1.197s
tests_1  | Ran all test suites.
tests_1  | 
```

If we change the tests:

```
tests_1  | PASS src/App.test.js
tests_1  |   ✓ renders without crashing (4ms)
tests_1  |   ✓ is true (1ms)
tests_1  | 
tests_1  |   console.log src/App.test.js:12
tests_1  |     true
tests_1  | 
tests_1  | Test Suites: 1 passed, 1 total
tests_1  | Tests:       2 passed, 2 total
tests_1  | Snapshots:   0 total
tests_1  | Time:        0.243s, estimated 1s
tests_1  | Ran all test suites.
tests_1  | 
```

But still, the workflow is not ideal, we cannot interact with the tests, but to do that you will need to do `docker exec -it tests_1 sh` and run the tests by hand.