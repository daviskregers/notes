# Type Relations

Now we have 2 different types - book and author. We can introduce relations that will between those objects.

We can define a relation in the data.

```js
var books = [
        {name: "Name of the Wind", genre: "Fantasy", id: '1', authorId: '1'},
        {name: "The Final Empire", genre: "Fantasy", id: '2', authorId: '2'},
        {name: "The Long Earth", genre: "Sci-Fi", id: '3', authorId: '3'}
];
```

And then add a field to the `BookType`.

```js
const BookType = new GraphQLObjectType({
        name: 'Book',
        fields: () => ({
                id: { type: GraphQLID },
                name: { type: GraphQLString },
                genre: { type: GraphQLString },
                author: { 
                        type: AuthorType, 
                        resolve(parent, args) {
                                return _.find(authors, {id: parent.authorId });
                        }
                }
        })
});
```

Now we test a query

```
{
  book(id: 1) {
    id
    name
    genre
    author {
      id
      name
      age
    }
  }
}

---

{
    "data": {
        "book": {
            "id": "1",
            "name": "Name of the Wind",
            "genre": "Fantasy",
            "author": {
                "id": "1",
                "name": "Patric Rothfuss",
                "age": 44
            }
        }
    }
}
```