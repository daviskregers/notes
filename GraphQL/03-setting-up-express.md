# Setting up express

We are going to create a new project directory.


```
➜  projects cd learning 
➜  learning mkdir graphql
➜  learning cd graphql 
➜  graphql git init
```

In it, we are going to make an express.js server app:

```
➜  graphql git:(master) mkdir server
➜  graphql git:(master) cd server   
➜  server git:(master) npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help json` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (server) 
version: (1.0.0) 
description: 
entry point: (index.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
About to write to /home/davis/projects/learning/graphql/server/package.json:

{
  "name": "server",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes) 
➜  server git:(master) ✗ npm i express --save
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN server@1.0.0 No description
npm WARN server@1.0.0 No repository field.

+ express@4.17.1
added 50 packages from 37 contributors and audited 126 packages in 2.306s
found 0 vulnerabilities

```

Then we are going to create an app.js file in the server directory:

```js
// IMPORTS
const express = require('express');

// CONSTANTS
const app = express();
const APP_PORT= 4000;

// LOGIC
app.listen(APP_PORT, () => console.log(`Listening for requests on port ${APP_PORT}`));
```

An if we run it:

```
➜  server git:(master) ✗ node app.js 
Listening for requests on port 4000
```

