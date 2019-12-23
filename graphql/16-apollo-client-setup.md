# Apollo Client Setup

We are going to use `Apollo` as a client to the GraphQL endpoint. It will query our node.js server from react.

```
➜  client git:(master) ✗ npm i apollo-boost react-apollo graphql --save
npm WARN tsutils@3.17.1 requires a peer of typescript@>=2.8.0 || >= 3.2.0-dev || >= 3.3.0-dev || >= 3.4.0-dev || >= 3.5.0-dev || >= 3.6.0-dev || >= 3.6.0-beta || >= 3.7.0-dev || >= 3.7.0-beta but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/jest-haste-map/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/chokidar/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.2 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.2: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

+ graphql@14.5.8
+ apollo-boost@0.4.7
+ react-apollo@3.1.3
added 27 packages from 22 contributors and audited 906623 packages in 27.466s

32 packages are looking for funding
  run `npm fund` for details

found 0 vulnerabilities
```

Now we are going to modify the App.js to use the apollo and inject it into our application.

```js
import React from 'react';
import BookList from './components/BookList';
import { ApolloProvider } from 'react-apollo';

// components
import ApolloClient from 'apollo-boost';

// apollo client setup
const client = new ApolloClient({
        uri: 'http://localhost:4000/graphql',
});

function App() {
  return (
          <ApolloProvider client={client}>
                  <div id="main">
                        <h1>Reading List</h1>
                        <BookList />
                  </div>
          </ApolloProvider>
  );
}

export default App;
```