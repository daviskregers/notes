# S3 Event Notificaitons Hands On

We can configure the notifications at `Properties -> Event Notifications`.

First, we create an event name and the prefix/suffix.

![](2022-02-17-08-00-02.png)

Then we can select all the event types which we want to use:

![](2022-02-17-08-00-32.png)

Then we can select a destination where the notifications will be sent into.

![](2022-02-17-08-00-59.png)

When using an SQS queue, make sure that the access policy is set up to allow the SendMessage from the bucket.