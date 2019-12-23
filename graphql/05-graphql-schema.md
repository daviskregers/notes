# Defining GraphQL Schema

Now that we have imported the GraphQL in our project, we need to start making a schema for it.

We are going to make a directory `schema` in the server and add a `schema.js` file in it:

```js
// IMPORTS
const graphql = require('graphql');

// CONSTANTS
const { GraphQLObjectType, GraphQLString } = graphql

// DEFINE OBJECT TYPES
const BookType = new GraphQLObjectType({
        name: 'Book',
        fields: () => ({
                id: { type: GraphQLString },
                name: { type: GraphQLString },
                genre: { type: GraphQLString }
        })
});
```

This file contains all the object types we are going to be using with defined fields and their types as well as the root queries that are going to be looked at in the next section.