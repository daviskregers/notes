# Mutations

Since we don't have any data in our database, it is a perfect time to setup mutations, to insert that data.

```js
const Mutation = new GraphQLObjectType({
        name: 'Mutation',
        fields: {
                addAuthor: {
                        type: AuthorType,
                        args: {
                                name: { type: GraphQLString },
                                age: { type: GraphQLInt },
                        },
                        resolve(parent, args) {
                                const author = new Author({
                                        name: args.name,
                                        age: args.age
                                });
                                author.save();
                        }
                },
                addBook: {
                        type: BookType,
                        args: {
                                name: { type: GraphQLString },
                                genre: { type: GraphQLString },
                                authorId: { type: GraphQLID }
                        },
                        resolve(parent, args) {
                                const book = new Book({
                                        name: args.name,
                                        genre: args.genre,
                                        authorId: args.authorId
                                });
                                book.save();
                        }
                }
        }
});

module.exports = new GraphQLSchema({
        query: RootQuery,
        mutation: Mutation
});
```

Now if we post the data:

```graphql
mutation {
    addAuthor(name: "Shaun", age: 30) {
        id
        name
        age
    }
}
```

We are going to get a response of:

```json
{
    "data": {
        "addAuthor": null
    }
}
```

But, in the mongodb, it has added it.

![](2019-12-23-12-50-47.png)

The reason why it does not return the data, is because we haven't returned anything from the resolve function.

```js
const Mutation = new GraphQLObjectType({
        name: 'Mutation',
        fields: {
                addAuthor: {
                        type: AuthorType,
                        args: {
                                name: { type: GraphQLString },
                                age: { type: GraphQLInt },
                        },
                        resolve(parent, args) {
                                const author = new Author({
                                        name: args.name,
                                        age: args.age
                                });
                                return author.save();
                        }
                },
                addBook: {
                        type: BookType,
                        args: {
                                name: { type: GraphQLString },
                                genre: { type: GraphQLString },
                                authorId: { type: GraphQLID }
                        },
                        resolve(parent, args) {
                                const book = new Book({
                                        name: args.name,
                                        genre: args.genre,
                                        authorId: args.authorId
                                });
                                return book.save();
                        }
                }
        }
});

module.exports = new GraphQLSchema({
        query: RootQuery,
        mutation: Mutation
});
```

![](2019-12-23-12-52-56.png)
![](2019-12-23-13-07-06.png)

Now we can query this:

![](2019-12-23-13-05-39.png)

![](2019-12-23-13-06-16.png)