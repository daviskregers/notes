# Lambda Monitoring & X-Ray Tracing

## Lambda Logging & Monitoring

- CloudWatch Logs
    - AWS Lambda execution logs are stored in AWS CloudWatch Logs
    - Make sure your AWS Lambda functions has an execution role with an IAM policy that authorizes writes to CloudWatch Logs
- CloudWatch Metrics
    - AWS Lambda metrics are displayed in AWS CloudWatch Metrics
    - Invocations, Durations, Concurrent Executions
    - Error count, Success Rates, Throttles
    - Async Delivery Failures
    - Iterator Age (Kinesis & DynamoDB Streams)

## Lambda Tracing with X-Ray
- Enable in Lambda configuration (Active Tracing)
- Runs the X-Ray daemon for you
- Use AWS X-Ray SDK in Code
- Ensure Lambda Function has a correct IAM Execution Role
    - The managed policy is called AWSXRayDaemonWriteAccess
- Environment variables to communicate with X-Ray
    - _X_AMZN_TRACE_ID: contains the tracing header
    - AWS_XRAY_CONTEXT_MISSING: by default, LOG_ERROR
    - AWS_XRAY_DAEMON_ADDRESS: the X-Ray Daemon IP_ADDRESS:PORT