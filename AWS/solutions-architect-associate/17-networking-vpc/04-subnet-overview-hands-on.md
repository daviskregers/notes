# Subnet overview hands on

We are navigating to subnets section and creating a new public subnet with 256 IP addresses ON AZ-A.

![](2020-01-01-16-08-35.png)

Then the same thing for AZ-B (change the Availability zone and CIDR block)

![](2020-01-01-16-10-06.png)

Then a Private Subnet A with 4096 IPs and a Private Subnet B.

![](2020-01-01-16-11-40.png)

![](2020-01-01-16-13-03.png)

---

When created, we notice that there are less available IPs than it should. This is because AWS reserves 5 IP addresses (first 4 and last 1 IP) in each subnet.
- These 5 IPs are not available for use and cannot be assigned to an instance
- Ex, if CIDR block 10.0.0.0/24 reserved IP are:
    - 10.0.0.0 - network address
    - 10.0.0.1 - reserved by AWS for the VPC router
    - 10.0.0.2 - reserved by AWS for mapping to Amazon-provided DNS
    - 10.0.0.3 - reserved by AWS for future use
    - 10.0.0.255 - Network broadcast address. AWS does not support broadcast in a VPC, therefore the address is reserved. 

![](2020-01-01-16-14-35.png)
- Tip:
    - If you need 29 IP addresses for EC2 instances, you can't choose a subnet of size /27 (32 IPs)
    - You need at least 64 IP, Subnet size /26 (64-5=59 > 29, but 32-5=27<29)