# VPC Summary

- CIDR - IP Range
- VPC - Virtual Private Cloud => We define a list of IPv4 & IPv6 CIDR
- Subnets - tied to an AZ, we define a CIDR
- Internet Gateway - at the vpc level provide IPv4 & IPv6 internet access
- Route Tables - must be edited to add routes from subnets to the IGS, VPC peering connections, VPC endpoints etc
- NAT Instances - gives internet access to instances in private subnets. Old, must be setup in a public subnet, disable Source / Destination check flag.
- NAT Gateway - managed by AWS, provides scalable internet access to private isntances, IPv4 only
- Private DNS + Route 53 - aenable DNS resolution + DNS hostnames (VPC)
- NACL - stateless, subnet rules for inbount and outbound, don't forget ephemeral ports
- Security Groups: Statefule, operate at the EC2 instance level
- VPC Peering: Connect two VPC with non overlapping CIDR non transitive
- VPC Endpoints: Provide private access to AWS Services (S3, DynamoDB, CloudFormation, SSM) within VPC
- VPC FLow Logs: Can be setup at the VPC / Subnet / ENI Level for ACCEPT and REJECT traffic, helps identifying attacks, analyze using Athena or CloudWatch Log Instights
- Bastion Host: Public instance to ssh into, that has SSH connectivity to instances in private subnets
- Site to Site VPN: Setup a Customer Gateway on DC, a Virtual Private Gateway on VPC, and site-to-site VPN over public internet
- Direct Connect: Setup a Virtual Private Gateway on VPC, and establish a direct private connection to an AWS Direct Connect Location
- Direct Connect Gateway: setup a Direct Connect to many VPC in different regions
- Internet Gateway Egress: like a NAT Gateway, but for IPv6