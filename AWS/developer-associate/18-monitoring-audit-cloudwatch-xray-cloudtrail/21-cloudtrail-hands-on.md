# CloudTrail Hands On

We can open up CloudTrail and use filters to see when an instance was terminated.

![](2022-04-26-18-12-59.png)

Here we can see that 2 instances were terminated by root, one by Cloud9 and one by AutoScaling.

We can also check for Read-only events etc.

![](2022-04-26-18-14-28.png)

---

## Trails

You can create a trail to capture more events.

![](2022-04-26-18-16-21.png)

![](2022-04-26-18-17-10.png)

![](2022-04-26-18-17-48.png)

![](2022-04-26-18-18-49.png)

![](2022-04-26-18-18-58.png)

Event source options are S3 and Lambda.

![](2022-04-26-18-20-04.png)

![](2022-04-26-18-20-45.png)

![](2022-04-26-18-20-56.png)

![](2022-04-26-18-21-22.png)

We can see that the CloudTrail is also created in CloudWatch now.

![](2022-04-26-18-22-08.png)

You can also view the events in S3 bucket or create an Athena table from the s3 bucket and query them.