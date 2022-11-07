# Default VPC overview

- All new accounts have a default VPC
- New instances are launched into default VPC is no subnet is specified
- Default VPC have internet connectivity and all instances have public IP
- We also get a public and a private DNS name

![](2020-01-01-15-49-19.png)

Our account has one default VPC, available hosts - 65536.

![](2020-01-01-15-50-23.png)

Has 3 subnets - 3 availability zones, each has 4091 availabl IPs.

![](2020-01-01-15-51-37.png)

We have a VPC route table, which defines that one of the IPs has an internet gateway

![](2020-01-01-15-54-01.png)

and has associations to our 3 availability zone subnets

![](2020-01-01-15-54-34.png)

Then our 3 availability zones allow all inbound traffic and all outbound traffic (through network ACL):

![](2020-01-01-15-55-44.png)

![](2020-01-01-15-55-55.png)