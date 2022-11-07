# Other useful AWS services

## SNS

Send push notification, sms to mobile devices etc.
You can also listen to sns notifcations to trigger lambdas.

AWS SNS: https://aws.amazon.com/sns/

## SES

E-mail sending service.

AWS SES: https://aws.amazon.com/ses/

## SQS

Message queues. Push certain jobs onto a queue, run a lambda function that runs, pulls an item from a queue and processes it.

AWS SQS: https://aws.amazon.com/sqs/

## AWS Step Functions

Orchestrate lambda functions. Build bigger functions with multiple lambda functions 
    - run multiple in parallel
    - branching - if one lambda fails, run another one
    - sequential - run one lambda after another

AWS Step Functions: https://aws.amazon.com/step-functions/

## Kinesis

If you have something that constantly streams data. This bundles it and
processes it into a structured data.

AWS Kinesis: https://aws.amazon.com/kinesis/

## IAM

Handle access control

## CloudWatch

View logs, set up scheduled triggers.

AWS CloudWatch: https://aws.amazon.com/cloudwatch/

## CodeBuild, CodePipeline

When you have bigger projects, you might want to create a pipeline, where everything builds, deploys on commiting code into git.

AWS CodeBuild: https://aws.amazon.com/codebuild/

AWS CodePipeline: https://aws.amazon.com/codepipeline