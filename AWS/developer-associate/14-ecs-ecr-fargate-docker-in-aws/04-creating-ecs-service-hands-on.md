# Creating ECS Service - Hands On

In order to launch a service, first we need to create an ECS task definition.

![](2022-04-20-09-12-48.png)

We are going to use `nginxdemos/hello` image for the container.

![](2022-04-20-09-14-06.png)

For the environment, we can choose whether to run it on Fargate or EC2 instances. We can also choose the OS, CPU, Memory, Role, Network.

![](2022-04-20-09-15-49.png)

We can configure storage - how much storage do we need or adding volumes.

![](2022-04-20-09-17-16.png)

We can also configure monitoring and logging.

![](2022-04-20-09-17-53.png)

Next we want to run this task definition as a service behind a load balancer. For that to work, we need to define 2 security groups.

One that allows the load balancer to connect to the port 80.

![](2022-04-20-09-21-19.png)

And one for the ECS task.

![](2022-04-20-10-01-00.png)
![](2022-04-20-10-22-07.png)

Now we can open up the ECS cluster, open up our demo-cluster and click on deploy.

![](2022-04-20-10-02-53.png)

We are also going to use a Load Balancer.

![](2022-04-20-10-04-03.png)

For the networking - we are going to use a nginx-demo-sg security group.

![](2022-04-20-10-05-01.png)

We are going to modify the ALB, and set the alb-ecs-sg security group for it.

![](2022-04-20-10-17-07.png)

Now we see that the task is running:

![](2022-04-20-10-25-17.png)

If we open up the ALB url:

![](2022-04-20-10-28-32.png)

Now we can open up our service, click on edit and scale it up:

![](2022-04-20-10-29-39.png)

We'll see them provisioning.

![](2022-04-20-10-31-54.png)

And if we refresh the ALB url, we'll see different IDs.

![](2022-04-20-10-32-22.png)

![](2022-04-20-10-32-29.png)