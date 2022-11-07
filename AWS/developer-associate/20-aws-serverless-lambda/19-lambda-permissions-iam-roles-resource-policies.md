# Lambda Permissions - IAM Roles & Resources Policies

## IAM Role

- Grants the Lambda Function permissions to AWS services / resources
- Sample managed policies for Lambda:
    - AWSLambdaBasicExecutionRole - Upload logs to CloudWatch
    - AWSLambdaKinesisExecutionRole - Read from Kinesis
    - AWSLambdaDynamoDBExecutionRole - Read from DynamoDB Streams
    - AWSLambdaSQSQueueExecutionRole - Read from SQS
    - AWSLambdaVPCAccessExecutionRole - Deploy Lambda function in VPC
    - AWSXRayDaemonWriteAccess - Upload trace data to X-Ray
- When you use an event source mapping to invoke your function, Lambda uses the execution role to read event data.
- Best practice: create one Lambda Execution Role per function.

## Resource Based Policies

- use resource-based policies to give other accounts and AWS services permission to use your Lambda resources
- Similar to S3 bucket policies for S3 bucket
- An IAM principal can access Lambda:
    - If the IAM policy attached to the principal authorizes it (e.g. user access)
    - Or if the resource-based policy authorizes (e.g. service access)
- When AWS service like Amazon S3 calls your Lambda function, the resource based policy gives it access.