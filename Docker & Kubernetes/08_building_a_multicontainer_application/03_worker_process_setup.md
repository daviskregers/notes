# Worker process setup

We'll create a new project directory and a worker directory in it:

```
davis@davis-arch  ~/projects/docker   master  mkdir 06_building_a_multicontainer_application
davis@davis-arch  ~/projects/docker   master  cd 06_building_a_multicontainer_application 
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  mkdir worker
```

In the worker directory we create a `package.json` file:

```json
{
    "dependencies": {
        "nodemon": "1.18.10",
        "redis": "2.8.0"
    },
    "scripts": {
        "start": "node index.js",
        "dev": "nodemon"
    }
}
```

And `index.js` file:

```js
const keys = require('./keys');
const redis = require('redis');

const redisClient = redis.createClient({
    host: keys.redisHost,
    port: keys.redisPort,
    retry_strategy: () => 1000 // automatically reconnect once every 1 second if connection lost
});

const sub = redisClient.duplicate();

function fib(index) {
    if( index < 2) return 1;
    return fib(index - 1) + fib(index - 2);
}

sub.on('message', (channel, message) => {
  redisClient.hset('values', message, fib(parseInt(message)));
});

sub.subscribe('insert'); // subscribe to insert messages
```

And `keys.js` file:

```js
module.exports = {
    redisHost: process.env.REDIS_HOST,
    redisPort: process.env.REDIS_PORT
}
```