# GraphQL lists

Now that we have defined relation between book and it's author. We might want to define a relation the other way around. But it is a one to many relation, which will need to return a list of all the books of that author.

First, we are going to add more books:

```js
var books = [
    {name: "Name of the Wind", genre: "Fantasy", id: '1', authorId: '1'},
    {name: "The Final Empire", genre: "Fantasy", id: '2', authorId: '2'},
    {name: "The Long Earth", genre: "Sci-Fi", id: '3', authorId: '3'},
    {name: "The Hero of Ages", genre: "Fantasy", id: '4', authorId: '3'},
    {name: "The Colour of Magic", genre: "Fantasy", id: '5', authorId: '3'},
    {name: "The Light Fantastic", genre: "Fantasy", id: '6', authorId: '3'}
];
```

Then, we are going to define a relation with a type of a list of `BookType`.

```js
const AuthorType = new GraphQLObjectType({
        name: 'Author',
        fields: () => ({
                id: { type: GraphQLID },
                name: { type: GraphQLString },
                age: { type: GraphQLInt },
                books: {
                        type: new GraphQLList(BookType),
                        resolve(parent, args) {
                                return _.filter(books, { authorId: parent.id });
                        }
                }
        })
});
```

Now we can query it:

```
{
  author(id: 3) {
    id
    name
    age
    books {
      id
      name
      genre
    }
  }
}

---

{
    "data": {
        "author": {
            "id": "3",
            "name": "Terry Pratchett",
            "age": 66,
            "books": [
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
}

```