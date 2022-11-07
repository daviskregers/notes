# Lambda Event Source Mapping Hands On

We are going to create a new lambda function and a new SQS queue.
Then in a lambda function, we are going to add the SQS trigger.

![](2022-05-12-08-10-21.png)

You might also need to setup permissions for this as well.

![](2022-05-12-08-11-01.png)

In order to set it up, we need to attach the `AWSLambdaSQSQueueExecutionRole` permissions to the lambda execution role.