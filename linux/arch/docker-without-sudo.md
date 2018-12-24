# Docker command without sudo

The problem with docker is that whenever you add the `docker` group to the user, it basically becomes a root user. And when that is dome, several applications might not work saying that it is unsafe to run them as root.

We can use ACLs to fix this.

```bash
sudo setfacl -m davis:rwx /var/run/docker.sock
```

![](../../images/2018-12-24-18-01-21.png)

Note that this should be used only in local setups, not in production.

[Reference to AskUbuntu](https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo#answer-982187)