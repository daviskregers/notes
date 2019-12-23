# Add book component

We create a new component `AddBook`, bring out queries to their own file.

```js
const addBookMutation = gql`
mutation($name: String!, $genre: String!, $authorId: ID!) {
        addBook(name: $name, genre: $genre, authorId: $authorId) {
                name
                id
        }
}
`
```

```js
import React, { Component } from 'react';
import { graphql } from 'react-apollo';
import { compose } from 'recompose';
import { getAuthorsQuery, addBookMutation, getBooksQuery } from '../queries/queries';

class AddBook extends Component {

        constructor(props) {
                super(props);
                this.state = {
                        name: '',
                        genre: '',
                        authorId: '',
                };
        }

        displayAuthors() {

                if(this.props.getAuthorsQuery.loading) {
                        return (<option>Loading authors...</option>);
                }

                return this.props.getAuthorsQuery.authors.map(author => {
                        return (<option key={author.id} value={author.id}>{author.name}</option>);
                });

        }

        submitForm(e) {
                e.preventDefault();
                this.props.addBookMutation({
                        variables: {
                                name: this.state.name,
                                genre: this.state.genre,
                                authorId: this.state.authorId
                        },
                        refetchQueries: [
                                { query: getBooksQuery }
                        ]
                });
        }

        render() {
                return (
                        <form id="add-book" onSubmit={ this.submitForm.bind(this) }>
                                <div className="field">
                                        <label>Book name:</label>
                                        <input type="text" onChange={ (e) => this.setState({ name: e.target.value }) } />
                                </div>
                                <div className="field">
                                        <label>Genre:</label>
                                        <input type="text" onChange={ (e) => this.setState({ genre: e.target.value }) } />
                                </div>
                                <div className="field">
                                        <label>Author:</label>
                                        <select onChange={ (e) => this.setState({ authorId: e.target.value }) }>
                                                <option>Select author</option>
                                                { this.displayAuthors() }
                                        </select>
                                </div>
                                <button>+</button>
                        </form>
                );
        }
}

export default compose(
        graphql(getAuthorsQuery, {name: 'getAuthorsQuery'}),
        graphql(addBookMutation, {name: 'addBookMutation'})
)(AddBook);
```

Note that we are using `compose` since we have multiple queries bound to the component. Each has name and result will be stored at the `this.props.{queryName}`.

Also, when calling the mutation the `refetchQueries` is used to refetch the list of the books in the `BookList` component on form submission.