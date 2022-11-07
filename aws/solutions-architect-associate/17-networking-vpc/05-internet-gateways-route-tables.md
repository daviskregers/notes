# Internet Gateways & Route tables

If we want to create an EC2 instance in the subnet with a public IP address, we need to modify the public subnet to auto-assign IPs.

![](2020-01-01-16-21-21.png)

![](2020-01-01-16-21-37.png)

![](2020-01-01-16-22-39.png)

When created, we can see that we have a private IP of `10.0.0.250` and a public IP of `54.246.162.86`.

![](2020-01-01-16-26-33.png)

Now, even though our security group allows this, if we were to try to connect to it via ssh, the connection would time out.

This is because the subnet does not have an internet gateway.

## Internet Gateways

- Internet Gateways help our VPC instances connect with the internet
- It scales horizaontally and is HA and redundant
- Must be created separately from VPC
- One VPC can only have attached to one IGW and vice versa
- Internet Gateway is also a NAT for the instances that have a public IPv4
- internet gateways on their own do not allow internet access
- Route tables must also be edited

## Creating an Internet Gateway

![](2020-01-01-16-29-41.png)

It will show as detached

![](2020-01-01-16-30-12.png)

![](2020-01-01-16-30-24.png)

![](2020-01-01-16-30-43.png)

![](2020-01-01-16-31-08.png)

Now if we would try to ssh, it still wouldn't work, because we have to edit the Route Table.

## Editing Route tables

We are going to create a public route table for public subnets.

![](2020-01-01-16-32-23.png)

And a private Route Table For private subnets.

![](2020-01-01-16-33-07.png)

Then, we want to edit the associations and add public subnets to the public route table, private to private.

![](2020-01-01-16-35-32.png)

Then we are going to edit the routes of the public route table and add IGW.

![](2020-01-01-16-36-49.png)

![](2020-01-01-16-37-04.png)

Now, we can connect to the SSH.