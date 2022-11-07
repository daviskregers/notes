# Lambda in VPC Hands On

We are going to create an empty security group in EC2.
Then, in Lambda, we can go to `Configuration - VPC` and set it up:

![](2022-05-12-08-55-40.png)

![](2022-05-12-08-55-56.png)

This will fail because the lambda execution role doesn't have CreatenetworkInterface permission.

![](2022-05-12-08-56-39.png)

So, we need to attach this permission to the execution role.

![](2022-05-12-08-57-11.png)

After that's done, we can see the new network interfaces in `EC2 - Network Interfaces`.

![](2022-05-12-08-58-02.png)