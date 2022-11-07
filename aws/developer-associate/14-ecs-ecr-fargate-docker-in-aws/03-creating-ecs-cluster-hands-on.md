# ECS Cluster - Hands On

We can go into the ECS Container Service to start working on it.

![](2022-04-20-08-58-33.png)

We are going to create our first cluster.

![](2022-04-20-09-00-47.png)

We are going to fill out the creating form. We are going to choose a name for it and the default VPC, subnets.

![](2022-04-20-09-01-47.png)

For infrastructure the default option is the Fargate, but we can select to use the EC2 instances as well. There is also an external instances option where you can configure external instances like on premises.

![](2022-04-20-09-04-18.png)

There is also an option to configure monitoring and tags, but we are going to leave it as is.

![](2022-04-20-09-05-06.png)

---

Since we selected the ECS cluster with EC2 ec2, we can go to Auto Scaling Groups and see it.

![](2022-04-20-09-06-46.png)

In the ECS we will see a cluster created with basically nothing deployed to it.

![](2022-04-20-09-07-41.png)

In the infrastructure tab we'll see ithat there are 3 providers. We have FARGATE, FARGATE_SPOT and our ASGProvider.

![](2022-04-20-09-09-08.png)

If we were to increase the minimum capacity of the ASG instances to 1, it will automatically register it in the container instances.

![](2022-04-20-09-09-58.png)

![](2022-04-20-09-10-50.png)

Now we can see that it is also registered on ECS.

![](2022-04-20-09-11-11.png)