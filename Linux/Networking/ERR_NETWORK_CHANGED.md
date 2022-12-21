---
Created: 2022-11-28 15:55:27
Modified: Sunday 27th November 2022 15:55:23
Type: article
Source: https://superuser.com/questions/747735/regularly-getting-err-network-changed-errors-in-chrome
Tags: [development/linux/networking, review]
Review: Hard
---


```console
sysctl -w net.ipv6.conf.all.disable_ipv6=1
sysctl -w net.ipv6.conf.default.disable_ipv6=1
```