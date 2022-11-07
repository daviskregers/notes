# Security Groups Hands On

We can go into `AWS EC2 -> Security Groups` to find our security groups. They are the way to control access to your EC2 instances.

![](2021-09-07-17-02-26.png)

The `launch-wizard-1` security group is a security group that was created when we launched an EC2 instance.

The `default` security group is created when your AWS account is created.

If we select the `launch-wizard-1` we can see that we have 3 bound rules:

![](2021-09-07-17-04-23.png)

And 1 outbound rule:

![](2021-09-07-17-04-50.png)

The inbound rules specify that we can connect to the machine by using HTTP (port 80) on both IPv4 and IPv6. As well as ssh into it via the port 2.

The outbound rules specify that everything is allowed to go out of the instance.

We can edit the rules by clicking on the `edit inbound|outbound rules` button next to the table.

If we were to delete the port 80 inbound rules, once we open our instance in our browser, it will get a timeout as the instance will not respond to us.

We can also open up ports by adding new entries:

![](2021-09-07-17-10-55.png)

We can select the type (port) as well as the source which can be from anywhere, can be specific IP addresses or even other security groups.