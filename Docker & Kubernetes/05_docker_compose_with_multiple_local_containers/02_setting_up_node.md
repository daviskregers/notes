# Setting up Node app

```
davis@davis-arch  ~/projects/docker   master  mkdir 03_visits
davis@davis-arch  ~/projects/docker   master  cd 03_visits 
davis@davis-arch  ~/projects/docker/03_visits   master  touch package.json
davis@davis-arch  ~/projects/docker/03_visits   master  touch index.js
```

package.json:

```json
{
    "dependencies":{
        "express": "~4.16.4",
        "redis": "~2.8.0"
    },
    "scripts": {
        "start": "node index.js"
    }
}
```

index.js:

```js
const express = require('express');
const redis = require('redis');

const app = express();
const client = redis.createClient();
client.set('visits', 0);

app.get('/', (req, res) => {
    client.get('visits', (err, visits) => {
        res.send('Visits: ' + visits);
        client.set('visits', parseInt(visits) + 1);
    });
});

app.listen(8080, () => {
    console.log('Listening on port 8080');
});
```