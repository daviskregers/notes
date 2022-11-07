# Docker compose files

We can create a `docker-compose.yml` file that contains all the options we'd normally pass to the docker-cli. With this project, we'll specify that we want docker to create 2 containers - redis and node server. The networking between them will be automatically set up.

```
 davis@davis-arch  ~/projects/docker/03_visits   master  touch docker-compose.yml
```

```yaml
version: '3'
services:
  redis-server:
    image: redis
  node-app:
    build: .
    ports:
      - 8080:8080
```

Change the index.js to connect to redis

```js
const express = require('express');
const redis = require('redis');

const app = express();
const client = redis.createClient({
    host: 'redis-server',
    port: 6379
});
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