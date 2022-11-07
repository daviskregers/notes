# Lambda Monitoring & X-Ray Tracing Hands On

In the lambda, under `Monitor - Metrics` we can see the CloudWatch Metrics for our lambda.

![](2022-05-12-08-44-37.png)

We can also see the CloudWatch Logs for the lambda invocations.

![](2022-05-12-08-45-18.png)

We can go to `Configuration - Monitoring and operations tools` 

![](2022-05-12-08-45-58.png)

We can enable AWS X-Ray there.

![](2022-05-12-08-46-26.png)

This will also create the necessary permissions:

![](2022-05-12-08-47-06.png)

Then, we can trigger the function and after some time we will see an xray service map.

![](2022-05-12-08-48-15.png)