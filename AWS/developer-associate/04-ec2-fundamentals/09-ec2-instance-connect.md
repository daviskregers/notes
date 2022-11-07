# EC2 Instance Connect

You can use an alternative to ssh for connecting to your ec2 instances - the EC2 Instance Connect.

In the EC2 Instances view you can select an instance and click on the connect button.

![](2021-09-07-17-47-25.png)

Then the first tab should be the `EC2 Instance Connect`.

![](2021-09-07-17-48-02.png)

This is going to open up a terminal to the EC2 instance:

![](2021-09-07-17-49-20.png)

Note that this still relies on SSH. If you have disabled the SSH inbound rules in your security groups - you will get a timeout.