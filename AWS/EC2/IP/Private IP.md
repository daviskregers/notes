---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/ip, review]
sr-due: 2022-12-12
sr-interval: 20
sr-ease: 250
---

## Private IP

- Private IP means the machine only be identified on a private network
- The IP must be unique across the private network
- But two different private networks (two companies) can have the same IPs
- Machines connect to internet through a gateway
- Only a specified range of IPs can be used as a private IP

    - 10.0.0.0 - 10.255.255.255 (10.0.0.0/8) - in big networks
    - 172.16.0.0 - 172.31.255.255 (172.16.0.0/12) - default AWS one
    - 192.168.0.0-192.168.255.255 (192.168.0.0/16) - example: home networks