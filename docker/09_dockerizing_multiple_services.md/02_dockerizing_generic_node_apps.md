# Dockerizing generic node apps

```
davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  touch server/Dockerfile.dev
 davis@davis-arch  ~/projects/docker/06_building_a_multicontainer_application   master  touch worker/Dockerfile.dev
```

For both `Dockerfile.dev`:

```Dockerfile
FROM node:alpine
WORKDIR "/app"
COPY ./package.json ./
RUN npm install
COPY . .
CMD ["npm", "run", "dev"]
```

