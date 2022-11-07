# Introduction

GraphQL is basically a powerfull query language that is used to communicate data between client and a server. 

It allows us to communicate data in a more flexible and efficient approach than RESTful approach would.

## RESTful approach

A RESTful approach would look something like this:

```

- Endpoint for getting a particular book:

    domain.com/books/:id
    title, genre, reviews, authorid

- Endpoint for getting the author info of that book:

    domain.com/authors/:id
    name, age, biography, booksids

```

Typically what we would do if we needed to get the author of the book - we would grab the id from the first request and then make a second request to get the author.

Then, we might also want to to get all the books of that particular author. With that we might need to call the books endpoint multiple times.

This starts to show the inefficiencies with RESTful approach.

## GraphQL approach

The GraphQL approach to this problem will look like this:

```qraphql

- Query to get book data and it's author data (AND other books):

    {
        book(id: 123) {
            title
            genre
            reviews
            author {
                name
                bio
                books {
                    name
                }
            }
        }
    }

```

The great thing about this approach is that we can get all the previously needed data with a single request and we can decide what fields do we need in order to not bloat the response.

