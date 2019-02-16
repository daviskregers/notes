# Generating the React app

```
 davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  create-react-app client

Creating a new React app in /home/davis/projects/docker/06_building_a_multicontainer_application/client.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts...

+ react-dom@16.8.2
+ react@16.8.2
+ react-scripts@2.1.5
added 1847 packages from 724 contributors and audited 36349 packages in 57.322s
found 63 low severity vulnerabilities
  run `npm audit fix` to fix them, or `npm audit` for details

Success! Created client at /home/davis/projects/docker/06_building_a_multicontainer_application/client
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd client
  npm start

Happy hacking!
```

Modify `package.json`

```json
{
  "name": "client",
  "version": "0.1.0",
  "private": true,
  "dependencies": {
    "react": "^16.8.2",
    "react-dom": "^16.8.2",
    "react-scripts": "2.1.5",
    "react-router-dom": "4.3.1",
    "axios": "0.18.0"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "eslintConfig": {
    "extends": "react-app"
  },
  "browserslist": [
    ">0.2%",
    "not dead",
    "not ie <= 11",
    "not op_mini all"
  ]
}
```

Create `src/OtherPage.js`:

```js
import React from 'react';
import {Link} from 'react-router-dom';

export default () => {
    return (
        <div>
            Im some other page!
            <link to="/">Go back home</link>
        </div>
    )
}
```

Create `src/Fib.js`:

```js
import React, {Component} from 'react';
import axios from 'axios';

class Fib extends Component {
    state = {
        seenIndexes: [],
        values: {},
        index: ''
    };

    componentDidMount() {
        this.fetchValues();
        this.fetchIndexes();
    }

    async fetchValues() {
        const values = await axios.get('/api/values/current');
        this.setState({values: values.data});
    }

    async fetchIndexes() {
        const seenIndexes = await axios.get('/api/values/all');
        this.setState({seenndexes: seenIndexes.data});
    }

    handleSubmit = async (event) => {
        event.preventDefault();
        await axios.post('/api/values', {
            index: this.state.index
        });
        this.setState({index: ''})
    }

    renderSeenIndexes() {
        return this.state.seenIndexes.map( ({number}) => number).join(', ');
    }

    renderValues() {
        
        const entries = [];
        for ( let key in this.state.values ) {
            entries.push(
                <div key={key}>
                    For index {key} I calculated {this.state.values[key]}
                </div>
            )
        }

    }

    render() {
        return (
            <div>
                <form onSubmit={this.handleSubmit}>
                    <label >Enter your index:</label>
                    <input 
                        value={this.state.index}
                        onChange={event => this.setState({index: event.target.value})}
                    />
                    <button>Submit</button>
                </form>

                <h3>Indexes I have seen</h3>
                { this.renderSeenIndexes() }

                <h3>Calculated values:</h3>
                {  this.renderValues() }

            </div>
        )
    }

}

export default Fib;
```

App.js

```js
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import {BrowserRouter as Router, Route, Link} from 'react-router-dom';
import OtherPage from './OtherPage';
import Fib from './Fib';

class App extends Component {
  render() {
    return (
      <Router>
        <div className="App">
          <header className="App-header">
            <img src={logo} className="App-logo" alt="logo" />
            <Link to="/">Home</Link>
            <Link to="/otherpage">Other Page</Link>
          </header>
          <div>
            <Route exact path = "/" component={Fib}/>
            <Route path="/otherpage" component={OtherPage} />}
          </div>
        </div>
      </Router>
    );
  }
}

export default App;
```