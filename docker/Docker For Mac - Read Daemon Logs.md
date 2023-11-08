---
tags:
  - review
  - type/idea
  - docker/logs
  - kubernetes/logs
  - docker/docker-for-mac/logs
Created: 2023-11-03 20:21
ID: 20231103202107
---
Tags: [[Docker]] [[Kubernetes]]

# Docker For Mac - Read Daemon Logs

```console
tail -f ~/Library/Containers/com.docker.docker/Data/log/vm/*
```

```
tail -f /Library/Containers/com.docker.docker/Data/log/vm/cri-dockerd.log
```

---
# References

- https://docs.docker.com/config/daemon/logs/