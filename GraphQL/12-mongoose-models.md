# Mongoose Models

Before we start putting data in the database, we will need to create Mongoose Schema that defines what data format we are going to use.

We are going to create a new directory `models` in the `server` directory and create two files: `book.js` and `author.js`.

```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;
const bookSchema = new Schema({
        name: String,
        genre: String,
        authorId: String,
        // id is not needed, mongodb creates that on it's own
});

module.exports = mongoose.model('Book', bookSchema);
```

```js
const mongoose = require('mongoose');
const Schema = mongoose.Schema;
const authorSchema = new Schema({
        name: String,
        age: Number,
});

module.exports = mongoose.model('Author', authorSchema);
```

Now we can remove the dummy hardcoded data from the `schema/schema.js` file as well as modify the resolve functions.

```
// IMPORTS
const graphql = require('graphql');
const Book = require('../models/book');
const Author = require('../models/author');

// CONSTANTS
const { 
        GraphQLObjectType, 
        GraphQLString, 
        GraphQLSchema,
        GraphQLID,
        GraphQLInt,
        GraphQLList
} = graphql

// DEFINE OBJECT TYPES
// DEFINE OBJECT TYPES                                                                                                             
const BookType = new GraphQLObjectType({                                                                                           
        name: 'Book',                                                                                                              
        fields: () => ({                                                                                                           
                id: { type: GraphQLID },                                                                                           
                name: { type: GraphQLString },                                                                                     
                genre: { type: GraphQLString },
                author: { 
                        type: AuthorType, 
                        resolve(parent, args) {
                                return Author.findById(parent.authorId);
                        }
                }
        })
});

const AuthorType = new GraphQLObjectType({
        name: 'Author',
        fields: () => ({
                id: { type: GraphQLID },
                name: { type: GraphQLString },
                age: { type: GraphQLInt },
                books: {
                        type: new GraphQLList(BookType),
                        resolve(parent, args) {
                                return Book.find({ authorId: parent.id });
                        }
                }
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
                                return Book.findById(args.id);
                        }
                },
                author: {
                        type: AuthorType,
                        args: { id: { type: GraphQLID } },
                        resolve(parent, args) {
                                return Author.findById(args.id);
                        }
                },
                books: {
                        type: new GraphQLList(BookType),
                        resolve(parent, args) {
                                return Book.find({});
                        }
                },
                authors: {
                        type: new GraphQLList(AuthorType),
                        resolve(parent, args) {
                                return Author.find({});
                        }
                }
        }
});


module.exports = new GraphQLSchema({
        query: RootQuery
});
```