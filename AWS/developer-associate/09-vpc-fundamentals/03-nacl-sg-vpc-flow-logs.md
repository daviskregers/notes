# Network ACL, Security Groups

## Network ACL
- A firewall which controls traffic from and to subnets
- Can have ALLOW and DENY rules
- Are attached at the Subnet level
- Rules only include IP addresses

## Security Groups
- A firewall that controls traffic to and from an ENI / an EC2 instance
- Can have only ALLOW rules
- Rules include IP addresses and other secutity groups

| **Security Group**                                                                                                                                           | **Network ACL**                                                                                                                                        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operates at the instance level                                                                                                                               | Operates at the subnet level                                                                                                                           |
| Supports allow rules only                                                                                                                                    | Supports allow and deny rules                                                                                                                          |
| Is stateful: return traffic is automatically allowed, regardless of any rules                                                                                | Is stateless: return traffic must be explicitly allowed by rules                                                                                       |
| We evaluate all rules before deciding whether to allow traffic                                                                                               | We process rules in number order when deciding whether to allow traffic                                                                                |
| Applies to an instance only if someone specifies the security group when launching the instance, or associates the security group with the instance later on | Automatically applies to all instances in the subnets it's associated with (therefore, you don't have to rely on users to specify the security groups) |

https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Security.html#VPC_Security_Comparison

# VPC Flow Logs

- Captures information about IP traffic going into your interfaces
    - VPC Flow Logs
    - Subnet Flow Logs
    - Elastic Network Interface Flow Logs
- Helps to monitor & troubleshoot connectivity issues:
    - Subnets to internet
    - Subnets to subnets
    - Internet to subnets
- Captures network information from AWS managed interfaces too: Elastic Load Balancers, ElastiCache, RDS, Aurora, etc.
- VPC Flow logs data can go to S3 / CloudWatch Logs