Possible solution for `ERR_NETWORK_CHANGED` errors on chrome when using docker:

```bash
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
```

At least it seems to be working for me.
