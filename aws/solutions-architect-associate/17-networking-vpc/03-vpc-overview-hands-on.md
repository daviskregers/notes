# VPC in AWS - IPv4

- VPC = Virtual Private Cloud
- You can have multiple VPCs in a region (max 5 per region, but you can place a support ticket to increase the amount)
- Max CIDR per VPC - 5. 
- For each CIDR: 
    - Min size is /28 = 16 IP addresses
    - Max is /16 = 65536 IP addresses
- Because VPC is private, only the Private IP ranges are allowed
    - 10.0.0.0 - 10.255.255.255 (10.0.0.0/8)
    - 172.16.0.0 - 172.31.255.255 (172.16.0.0/12)
    - 192.168.0.0 - 192.168.255.255 (192.168.0.0/16)
- Your VPC CIDR should not overlap with your other networks (ex: corporate)

## Hands on

We are going to create an empty VPC, without any wizard. To do this, we are going to navigate to `VPC -> Your VPCs` in Amazon Console.

![](images/2020-01-01-16-01-37.png)

In the tenancy option we are going to select default, this means that when that we launch EC2 instances, we are going to want shared hardware, not dedicated one that will cost us a lot more money.

When created, we can see that it also has a Main Route table and Main Network ACL created for us as well.

![](images/2020-01-01-16-03-43.png)

Also, we are not limited to only one CIDR Block, we can edit it and put multiple in it (up to 5 blocks).

![](images/2020-01-01-16-05-32.png)