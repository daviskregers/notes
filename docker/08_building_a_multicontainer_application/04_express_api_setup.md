# Express API setup

We'll make another directory in the project directory.

```
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  mkdir server
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  cd server
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application/server   master  touch package.json
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application/server   master  touch index.js
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application/server   master  touch keys.js
```

The `package.json`

```json
{
    "dependencies": {
        "express": "4.16.4",
        "pg": "7.8.0",
        "redis": "2.8.0",
        "cors":"2.8.5",
        "nodemon": "1.18.10"
    },
    "scripts": {
        "dev": "nodemon",
        "start": "node index.js"
    }
}
```

The `keys.js`

```js
module.exports = {
    redisHost: process.env.REDIS_HOST,
    redisPort: process.env.REDIS_PORT,
    pgHost: process.env.PGHOST,
    pgPort: process.env.PGPORT,
    pgDatabase: process.env.PGDATABASE,
    pgUser: process.env.PGUSER,
    pgPassword: process.env.PGPASSWORD,
}
```

The `index.js`

```js
const keys = require('./keys');

// Express App Setup
const express = require('express');
const bodyParser = require('body-parser');
const cors = require('cors');

const app = express();
app.use(cors());
app.use(bodyParser.json());

//  Postgres Client Setup
const { Pool } = require('pg');
const pgClient = new Pool({
    user: keys.pgUser,
    password: keys.pgPassword,
    database: keys.pgDatabase,
    host: keys.pgHost,
    port: keys.pgPort
});

pgClient.on('error', () => console.log('Lost PG connection'));
pgClient.query('CREATE TABLE IF NOT EXISTS values (number INT);').catch((err) => console.log(err));

// Redis Client Setup
const redis = require('redis');
const redisClient = redis.createClient({
    host: keys.redisHost,
    port: keys.redisPort,
    retry_strategy: () => 1000, // If connection lost, reconnect once every second
});

const redisPublisher = redisClient.duplicate();

// Express route handlers

app.get('/', (req, res) => {
    res.send('Hi');
});

app.get('/values/all', async (req ,res) => {
    const values = await pgClient.query('SELECT * FROM values');
    res.send(values.rows);
});

app.get('/values/current', async (req, res) => {
   redisClient.hgetall('values', (err, values) => {
       res.send(values);
   }) ;
});

app.post('/values', async (req, res) => {
    const index = req.body.index;
    
    if( parseInt(index)  > 40 ) {
        return res.status(422).send('Index too high');
    }

    redisClient.hset('values', index, 'Nothing yet!');
    redisPublisher.publish('insert', index);
    pgClient.query('INSERT INTO values(number) VALUES($1)', [index]);

    res.send({working: true});
});

app.listen(5000, err => {
    console.log('Listening');
})
```