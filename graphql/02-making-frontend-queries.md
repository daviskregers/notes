# Making frontend queries

In order to make a frontend query we can use a query in a structure like this:

```graphql
{
    books {
        name
        genre
        id
    }
}
```

It starts with a curly braces and in them we recursively define what fields to we want to get.

The response will be like this:

```json
{
    "data": {
        "books": [
            {
                "name": "The Final Empire",
                "genre": "Fantasy",
                "id": "5aa2906a9da47848141d622b"
            },
            ...
        ]
    }
}
```

Then, we can remove the ID field if not needed:

```graphql
{
    books {
        name
        genre
    }
}
```

And get a less bloated response:

```json
{
    "data": {
        "books": [
            {
                "name": "The Final Empire",
                "genre": "Fantasy",
            },
            ...
        ]
    }
}
```