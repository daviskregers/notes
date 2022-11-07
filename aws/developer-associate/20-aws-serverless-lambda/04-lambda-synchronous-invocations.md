# Lambda - Synchronous Invocations

- Synchronous - CLI, SDK, API Gateway, Application Load Balancer
    - Results are returned right away
    - Error handling must happen client side (retries, expenential backoff, etc)

![](2022-05-12-06-58-48.png)

- User Invoked
    - Elastic Load Balancing
    - Amazon API Gateway
    - Amazon CloudFront (Lambda@Edge)
    - Amazon S3 Batch
- Service Invoked
    - Amazon Cognito
    - AWS Step Functions
- Other Services
    - Amazon Lex
    - Amazon Alexa
    - Amazon Kinesis Data Firehose