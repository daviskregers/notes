# Setting up GraphQL

In the previously made backend express.js project we are going to install the following packages:

```zsh
➜  server git:(master) ✗ npm i graphql express-graphql --save
npm WARN server@1.0.0 No description
npm WARN server@1.0.0 No repository field.

+ express-graphql@0.9.0
+ graphql@14.5.8
added 6 packages from 5 contributors and audited 151 packages in 1.92s
found 0 vulnerabilities
```

Then we are going to modify the previously made `app.js` file:

```js
// IMPORTS
const express = require('express');
const graphqlHTTP = require('express-graphql');

// CONSTANTS
const app = express();
const APP_PORT= 4000;

// LOGIC

app.use('/graphql', graphqlHTTP({

}));

app.listen(APP_PORT, () => console.log(`Listening for requests on port ${APP_PORT}`));
```

Currently, if we visit the `/graphql` endpoint that will be used to query all the data, it will return an error like this:

```json
{"errors":[{"message":"GraphQL middleware options must contain a schema."}]}
```

This is because we haven't provided any schema to it. This will be done in the next steps.