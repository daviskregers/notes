# Default VPC overview

- All new accounts have a default VPC
- New instances are launched into default VPC is no subnet is specified
- Default VPC have internet connectivity and all instances have public IP
- We also get a public and a private DNS name

![](images/2020-01-01-15-49-19.png)

Our account has one default VPC, available hosts - 65536.

![](images/2020-01-01-15-50-23.png)

Has 3 subnets - 3 availability zones, each has 4091 availabl IPs.

![](images/2020-01-01-15-51-37.png)

We have a VPC route table, which defines that one of the IPs has an internet gateway

![](images/2020-01-01-15-54-01.png)

and has associations to our 3 availability zone subnets

![](images/2020-01-01-15-54-34.png)

Then our 3 availability zones allow all inbound traffic and all outbound traffic (through network ACL):

![](images/2020-01-01-15-55-44.png)

![](images/2020-01-01-15-55-55.png)