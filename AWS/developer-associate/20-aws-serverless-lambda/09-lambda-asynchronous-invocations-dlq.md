# Lambda Asynchronous Invocations & DLQ

- S3, SNS, CloudWatch Events
- The events are placed in an Event Queue
- Lambda attempts to retry on errors
    - 3 tries in total
    - 1 minute wait after 1st, then 2 minutes wait
- Make sure the processing is idempotent (in case of retries)
- If the function is retried, you will see duplicate logs entries in CloudWatch Logs
- Can define a DLQ (dead letter queue) - SNS or SQS - for failed processing (need correct IAM permissions)
- Asynchronous invocations allow you to speed up the processing if you don't need to wait for the result (ex: you need 1000 files processed)

![](2022-05-12-07-33-25.png)

## Services invocated asynchronously

- Amazon Simple Storage Service (S3)
- Amazon Simple Notification Service (SNS)
- Amazon CloudWatch Events / EventBridge
- AWS CodeCommit (CodeCommit Trigger: new branch, new tag, new push)
- AWs CodePipeline (invoke a Lambda function during the pipeline, Lambda must callback)
- other
- Amazon CloudWatch Logs (log processing)
- Amazon Simple Email Service
- AWS CloudFormation
- AWS Config
- AWS IoT
- AWS IoT Events
