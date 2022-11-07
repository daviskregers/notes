# Root Queries

By defining root queries we are going to define what queries we will have on our graphql that are not being relations - what are the root nodes of our objects that we are going to query.

```js
// IMPORTS
const graphql = require('graphql');

// CONSTANTS
const { GraphQLObjectType, GraphQLString, GraphQLSchema } = graphql

// DEFINE OBJECT TYPES
const BookType = new GraphQLObjectType({
        name: 'Book',
        fields: () => ({
                id: { type: GraphQLString },
                name: { type: GraphQLString },
                genre: { type: GraphQLString }
        })
});

// DEFINE ROOT QUERIES
const RootQuery = new GraphQLObjectType({
        name: 'RootQueryType',
        fields: {
                book: { 
                        type: BookType,
                        args: { id: { type: GraphQLString } },
                        resolve(parent, args) {
                                // code to get data from db or other source
                        }
                }
        }
})

module.exports = new GraphQLSchema({
        query: RootQuery
})
```

The `args` are provided to know what arguments are going to be passed to the root query.

The `resolve` function is a function that will describe on how we are going to get the data from database or other source.

---

Since we now have a valid schema built, we can also modify the `app.js`:

```js
// IMPORTS
const express = require('express');
const graphqlHTTP = require('express-graphql');
const schema = require('./schema/schema');

// CONSTANTS
const app = express();
const APP_PORT= 4000;

// LOGIC

app.use('/graphql', graphqlHTTP({
        schema
}));

app.listen(APP_PORT, () => console.log(`Listening for requests on port ${APP_PORT}`));
```

Now, when visiting the `/graphql` endpoint, we are going to get a message like this:

```json
{"errors":[{"message":"Must provide query string."}]}
```

The next step is to make a resolve function for the `BookType` so we can test it.