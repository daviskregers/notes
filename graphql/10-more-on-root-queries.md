# More on Root Queries

Previously we created root queries to fetch books and authors from given IDs. Now we might want to add root queries to fetch a list of all of the books and authors.

```js
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
                        resolve(parent, args) {
                                return _.find(authors, { id: args.id });
                        }
                },
                books: {
                        type: new GraphQLList(BookType),
                        resolve(parent, args) {
                                return books;
                        }
                },
                authors: {
                        type: new GraphQLList(AuthorType),
                        resolve(parent, args) {
                                return authors;
                        }
                }
        }
})
```

Now if we query it:

```
{
  books {
    id
    name
    genre
  }
}

---

{
    "data": {
        "books": [
            {
                "id": "1",
                "name": "Name of the Wind",
                "genre": "Fantasy"
            },
            {
                "id": "2",
                "name": "The Final Empire",
                "genre": "Fantasy"
            },
            {
                "id": "3",
                "name": "The Long Earth",
                "genre": "Sci-Fi"
            },
            {
                "id": "4",
                "name": "The Hero of Ages",
                "genre": "Fantasy"
            },
            {
                "id": "5",
                "name": "The Colour of Magic",
                "genre": "Fantasy"
            },
            {
                "id": "6",
                "name": "The Light Fantastic",
                "genre": "Fantasy"
            }
        ]
    }
}

```

```

{
  authors {
    id
    name
    age
  }
}


---

{
    "data": {
        "authors": [
            {
                "id": "1",
                "name": "Patric Rothfuss",
                "age": 44
            },
            {
                "id": "2",
                "name": "Brandon Sanderson",
                "age": 42
            },
            {
                "id": "3",
                "name": "Terry Pratchett",
                "age": 66
            }
        ]
    }
}

```