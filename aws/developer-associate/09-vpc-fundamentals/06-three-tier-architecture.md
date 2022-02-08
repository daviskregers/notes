# Three Tier Architecture

![](img/2022-02-08-08-06-31.png)

## LAMP Stack on EC2

- Linux: OS for EC2 Instances
- Apache: Web Server that runs on Linux (EC2)
- MySQL: database on RDS
- PHP: Application Logic (running on EC2)

---

- Can add Redis / Memcached (ElastiCache) to include caching
- To store local application data & software: EBS drive (root)

## Wordpress on AWS

![](2022-02-08-08-09-13.png)

## A more complicated wordpress setup

![](img/2022-02-08-08-11-11.png)

https://aws.amazon.com/blogs/architecture/wordpress-best-practices-on-aws/