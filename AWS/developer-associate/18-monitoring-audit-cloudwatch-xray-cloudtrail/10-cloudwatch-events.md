# CloudWatch Events

- Event Pattern: Intercept events from AWS services (Sources)
    - Example sources: EC2 Instance Start, CodeBuild Failure, S3, Trusted Advisor
    - Can intercept any API call with CloudTrail integration
- Schedule or Cron (example: create an event every 4 hours)

- A JSON payload is created from the event and passed to a target
    - Compute: Lambda, Batch, ECS task
    - Integration: SQS, SNS, Kinesis Data Streams, Kinsesis Data Firehose
    - Orchestration: Step Functions, CodePipeline, CodeBuild
    - Maintenance: SSM, EC2 Actions

In CloudWatch, on the left sidebar there is a section Rules

![](2022-04-26-16-59-01.png)

We can create a new rule

![](2022-04-26-16-59-53.png)

Every time an EC2 instance goes into a pending state, we create an event.

![](2022-04-26-17-00-22.png)

![](2022-04-26-17-00-40.png)

We are going to send an email from SNS with the entire event JSON

![](2022-04-26-17-02-45.png)

![](2022-04-26-17-03-58.png)


The rules that you create in CloudWatch events will also appear on EventBridge.

![](2022-04-26-17-04-41.png)

