# Book Details component

We are going to add a new component for getting book details.

```js
const getBookQuery = gql`
query($id: ID) {
        book(id: $id) {
                id
                name
                genre
                author {
                        id
                        name
                        age
                        books {
                                name
                                id
                        }
                }
        }
}
`
```

```js
import React, { Component } from 'react';
import { graphql } from 'react-apollo';
import { getBookQuery } from '../queries/queries';

class BookDetails extends Component {

        displayBookDetails() {
                const { book } = this.props.data;
                if(book) {
                        return (
                                <div>
                                        <h2>{ book.name }</h2>
                                        <p>{ book.genre }</p>
                                        <p>{ book.author.name }</p>
                                        <p>All books by this author</p>
                                        <ul>
                                                {
                                                        book.author.books.map(item => {
                                                                return <li key={item.id}>{item.name}</li>
                                                        })
                                                }
                                        </ul>
                                </div>
                        );
                }
                return (<div>No book selected</div>);
        }

        render() {
                return (
                        <div id="book-details">
                                { this.displayBookDetails() }
                        </div>
                );
        }
}

export default graphql(getBookQuery, {
        options: (props) => {
                return {
                        variables: {
                                id: props.bookId
                        }
                }
        }
})(BookDetails);
```

Note the export part, we are taking the prop and passing it to the graphql query as the ID param.

---

We'll modify the BookList.js file as well, it will call the component and pass the book id to it once clicked on the title.

```js
import React, { Component } from 'react';
import { graphql } from 'react-apollo';
import { getBooksQuery } from '../queries/queries';
import BookDetails from './BookDetails';

class BookList extends Component {

        constructor(props) {
                super(props);
                this.state = {
                        selected: null,
                }
        }

        displayBooks() {
                if(this.props.data.loading) {
                        return (<div>Loading books...</div>);
                }

                return this.props.data.books.map(book => {
                        return (<li onClick={ e => this.setState({selected: book.id}) } key={book.id}>{book.name}</li>)
                });

        }

        render() {
                return (
                        <div>
                                <ul id="book-list">
                                        { this.displayBooks() }
                                </ul>
                                <BookDetails bookId={ this.state.selected } />
                        </div>
                )
        }

}

export default graphql(getBooksQuery)(BookList);
```