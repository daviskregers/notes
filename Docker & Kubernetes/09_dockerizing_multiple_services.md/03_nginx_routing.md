# Nginx routing

Create a new service directory in the project called `nginx` and add a `default.conf` file:

```nginx
upstream client {
    server client: 3000;   
}

upstream api {
    server api:5000;
}

server {
    listen 80;
    location / {
        proxy_pass http://client;
    }
    location /api {
        rewrite /api/(.*) /$1 break;
        proxy_pass http://api;
    }
}
```

Create `Dockerfile.dev`:

```Dockerfile
FROM nginx
COPY ./default.conf /etc/nginx/conf.d/default.conf
```