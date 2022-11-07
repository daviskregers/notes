# VPC Peering

- Connect two VPC, privately using AWS network
- Make them behave as if they were in the same network
- Must not have overlapping CIDR (IP address ranges)
- VPC Peering connection is not transitive (must be established for each VPC that need to communicate with one another)

![](2022-02-08-07-57-29.png)

# VPC Endpoints

- Endpoints allow you to connect to AWS Services using a private network instead of the public www network
- This gives you enhanced security and lower latency to access AWS Services
- VPC endpoint gateway: S3 & DynamoDB
- VPC endpoint interface: the rest
- only used within your VPC

![](2022-02-08-07-59-23.png)

## Site to Site VPN

- Connect to an on-premises VPN to AWS
- The connection is automatically encrypted
- Goes over the public internet

## Direct Connect (DX)

- Establish a physical connection between on-premises and AWS
- The connection is private, secure and fast
- Goes over a private network
- Takes at least a month to establish

Note: Site-to-Site VPN and Direct Connect cannot access VPC endpoints.

![](2022-02-08-08-01-45.png)