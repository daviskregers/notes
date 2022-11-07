# GrapGL NonNull

We can use `GrapQLNonNull` function to validate that mutations require given fields, they cannot be null.

```js
const Mutation = new GraphQLObjectType({
        name: 'Mutation',
        fields: {
                addAuthor: {
                        type: AuthorType,
                        args: {
                                name: { type: new GraphQLNonNull(GraphQLString) },
                                age: { type: new GraphQLNonNull(GraphQLInt) },
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
                                name: { type: new GraphQLNonNull(GraphQLString) },
                                genre: { type: new GraphQLNonNull(GraphQLString) },
                                authorId: { type: new GraphQLNonNull(GraphQLID) }
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
```

![](2019-12-23-13-11-02.png)