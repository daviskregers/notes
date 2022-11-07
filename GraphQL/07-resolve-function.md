# Resolve Function

The resolve function describes the steps to take in order to retrieve the data we are querying for. The data can be fetched from a database or other source.

We are going to modify the schema file to resolve the data from a static object for now, add a second root query - authors.

```js
// IMPORTS
const graphql = require('graphql');
const _ = require('lodash')

// CONSTANTS
const { 
        GraphQLObjectType, 
        GraphQLString, 
        GraphQLSchema,
        GraphQLID,
        GraphQLInt
} = graphql

var books = [
        {name: "Name of the Wind", genre: "Fantasy", id: '1'},
        {name: "The Final Empire", genre: "Fantasy", id: '2'},
        {name: "The Long Earth", genre: "Sci-Fi", id: '3'}
];

var authors = [
        {name: "Patric Rothfuss", age: 44, id: '1'},
        {name: "Brandon Sanderson", age: 42, id: '2'},
        {name: "Terry Pratchett", age: 66, id: '3'}
];

// DEFINE OBJECT TYPES
const BookType = new GraphQLObjectType({
        name: 'Book',
        fields: () => ({
                id: { type: GraphQLID },
                name: { type: GraphQLString },
                genre: { type: GraphQLString }
        })
});

const AuthorType = new GraphQLObjectType({
        name: 'Author',
        fields: () => ({
                id: { type: GraphQLID },
                name: { type: GraphQLString },
                age: { type: GraphQLInt }
        })
});

// DEFINE ROOT QUERIES
const RootQuery = new GraphQLObjectType({
        name: 'RootQueryType',
        fields: {
                book: { 
                        type: BookType,
                        args: { id: { type: GraphQLID } },
                        resolve(parent, args) {
                                return _.find(books, { id: args.id });
                        }
                },
                author: {
                        type: AuthorType,
                        args: { id: { type: GraphQLID } },
                        resolve(paremt, args) {
                                return _.find(authors, { id: args.id });
                        }
                }
        }
})

module.exports = new GraphQLSchema({
        query: RootQuery
})

```

Now, if we query the `/graphql` endpoint:

```
{
  book(id: 1){
    id
    name
    genre
  }
}

---

{"data":{"book":{"id":"1","name":"Name of the Wind","genre":"Fantasy"}}}
```

```
{
  author(id: 1){
    id
    name
    age
  }
}

---

{"data":{"author":{"id":"1","name":"Patric Rothfuss","age":44}}}
```