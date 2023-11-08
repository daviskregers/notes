---
tags:
  - review
  - type/idea
  - docker/logs
Created: 2023-11-04 15:06
ID: 20231104150654
---
Tags: [[Docker]]

# Truncate Docker Container logs

```console
sudo truncate -s 0 $(sudo docker inspect --format='{{.LogPath}}' keycloak)
```

---
# References

- https://stackoverflow.com/a/42510314

