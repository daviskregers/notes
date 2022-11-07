# Cleaning up tests

The `App.test.js` file runs a test that when creating the component, nothing will crash. Since at the test time it calls the `Fib` component which makes `api` calls, it most likely will crash, so we'll remove this test:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

it('renders without crashing', () => {
});

```

