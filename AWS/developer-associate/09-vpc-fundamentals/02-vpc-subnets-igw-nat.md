# VPC, Subnets, IGW and NAT

## VPC and Subnets Primer

- VPC: private network to deploy your resources (regional resource)
- Subnets allow you to partition your network inside your VPC (Availability Zone Resource)
- A public subnet is a subnet that is accessible from the internet
- A private subnet is a subnet that is not accessible from the internet
- To define access to the internet and between subnets, we use Route Tables.

![](2022-02-08-07-43-32.png)

## Internet Gateway and NAT Gateways

- Internet Gateways help our VPC instances connect with the internet
- Public subnets have a route to the internet gateway

---

- NAT Gateways (AWS Managed) & NAT Instances (self-managed) allow your instances in your private subnets to access the internet while remaining private.

![](2022-02-08-07-46-26.png)