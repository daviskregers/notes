# VPC CheatSheet

- VPC: Virtual Private Cloud
- Subnets: Tied to an AZ, network parition of the VPC
- Internet Gateway / Instances: Give you internet access to private subnets
- NAT Gateway / Instances: give internet access to private subnets
- [[Network ACL]]: Sateless, subnet rules for inbount and outbound
- Security Groups: Stateful, operate at the EC2 instance level or ENI
- VPC Peering: Connect two VPC with non overlapping IP ranges, non transitive
- VPC Endpoints: Provide private access to AWS Services within VPC
- VPC Flow Logs: network traffic logs
- Site to Site VPN: VPN over public internet between on-premises DC and AWS
- Direct Connect: direct privat connection to AWS