# Security Groups & Classic Ports Overview

- Security Groups are fundamental of network security in AWS.
- They control how traffic is allowed into or out of our EC2 instances.
- The security groups only contain `allow` rules
- Security groups rules can reference by IP or by security group.

- Security groups are acting as a firewall on EC2 instances
- They regulate:
    - Access to ports
    - Authorized IP ranges - IPv4 and IPv6
    - Control of inbound network (from other to the instance)
    - Control of outbound network (from the instance to other)

- The security groups can be attached to multiple instances.
- Locked down to a region / VPC combination
- security groups live outside the EC21 - if traffic is blocked, the EC2 instance won't see it

- It's good to maintain one separate security group for SSH access
- If your application is not accessible (time out), it's a security group issue.
- If your application gives a "connection refused" error - it's an application error or it's not launched.

---

- All inbound traffic is blocked by default
- All outbound traffic is authorised by default