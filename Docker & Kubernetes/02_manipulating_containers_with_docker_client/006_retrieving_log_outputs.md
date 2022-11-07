# Retrieving log outputs

When using the `docker start`  without the `-a` flag and we want to see the output of the logs, we can use 

```
docker logs <container id>
```

```
davis@davis-arch  ~  docker create busybox echo hi there
c057588ee5fb84bbfb25c99935f6f2414e6ad2f42f69169cc4f86b36957ca1dc
 davis@davis-arch  ~  docker start c057588ee5fb84bbfb25c99935f6f2414e6ad2f42f69169cc4f86b36957ca1dc
c057588ee5fb84bbfb25c99935f6f2414e6ad2f42f69169cc4f86b36957ca1dc
 davis@davis-arch  ~  docker logs c057588ee5fb84bbfb25c99935f6f2414e6ad2f42f69169cc4f86b36957ca1dc
hi there
```