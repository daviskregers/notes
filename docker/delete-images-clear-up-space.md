# Delete docker images / clear up space

```
docker rmi -f $(docker images -f dangling=true -q)
```