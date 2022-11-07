# Opening websocket connections

React development server requires websocket connection, but our nginx does not allow it.  We'll modify the `default.conf` file to allow it:

```
upstream client {
    server client:3000;   
}

upstream api {
    server api:5000;
}

server {
    listen 80;
    location / {
        proxy_pass http://client;
    }
    location /sockjs-node {
        proxy_pass http://client;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "Upgrade";
    }
    location /api {
        rewrite /api/(.*) /$1 break;
        proxy_pass http://api;
    }
}
```

Now we can run `docker-compose up --build`.

