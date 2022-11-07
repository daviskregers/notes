# Lambda & S3 Event Notifications - Hands On

We are going to create a new S3 bucket. Once it's created we are going to properties and finding the Event notifications panel. Create a new event in it.

![](2022-05-12-07-52-06.png)

![](2022-05-12-07-52-26.png)

![](2022-05-12-07-52-46.png)

When viewing the Lambda, we can see that the S3 is now invoking it:

![](2022-05-12-07-53-18.png)

Now we can upload a file to the S3 Bucket and we'll see that the lambda will be invoked.