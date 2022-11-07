# Why mess with docker in the node?

- You can use the same debugging techniques we learned with docker CLI

```
docker logs container_id
docker exec -it container_id sh
...
```

- Manually kill containers to test kubernetes ability to `self-heal`

```
docker kill container_id
```

- Delete cached images in the node

```
docker system prune -a
```

