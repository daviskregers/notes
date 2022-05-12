# Lambda & Application Load Balancer Hands On

We are going to create a new function, this time we are choosing `Author from scratch` with a `Python 3.8` runtime.

Once the function is created, we are going to EC2 - Load Balancers and creating a new Application Load Balancer.

![](img/2022-05-12-07-17-40.png)

![](img/2022-05-12-07-18-31.png)

We are enabling it across 3 availability zones.

![](img/2022-05-12-07-18-59.png)

We are going to create a new security group.

![](img/2022-05-12-07-19-24.png)

Next, in routing we are choosing to create a new target group and target lambda functions.

![](img/2022-05-12-07-20-13.png)

Next, we are registering the target

![](img/2022-05-12-07-20-54.png)

![](img/2022-05-12-07-21-07.png)

If we are to open up the ALB url now, it will download the response JSON file.
In order for it to properly work, we need to change the response format:

![](img/2022-05-12-07-23-26.png)

Once deployed, it should work properly now:

![](img/2022-05-12-07-23-54.png)