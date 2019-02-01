# Node server setup

In this section we set up the node.js server:

```
davis@davis-arch  ~/projects/docker   master  mkdir 02_nodejs_web_server
 davis@davis-arch  ~/projects/docker   master  cd 02_nodejs_web_server 
```

Make a package.json
```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  touch package.json
```

With following content:

```json
{
    "dependencies": {
        "express": "~4.16.4"
    },
    "scripts": {
        "start": "node index.js"
    }
}
```

Make index.js:

```
davis@davis-arch  ~/projects/docker/02_nodejs_web_server   master  touch index.js
```

With content:

```js
const express = require('express');
const app = express();
app.get('/', (req, res) => {
    res.send('Hi there!');
});
app.listen(8080, () => {
    console.log('Listening on port 8080');
} );
```