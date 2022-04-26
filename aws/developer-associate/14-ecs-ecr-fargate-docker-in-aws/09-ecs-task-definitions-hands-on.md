# Task Definitions - Hands On

In the task definition we can define multiple containers.

![](img/2022-04-20-10-57-17.png)

We can also define whether it's essential or not. It means whether the task can continue running with the container being stopped.

For each container we can provide environment variables by defining them individually or by providing a file.

![](img/2022-04-20-10-59-09.png)

Currently via the console you cannot specify to use Parameter Store or Secrets Manager, but you can do it via the older version of the console, JSON format or CloudFormation.