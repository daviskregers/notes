# CloudTrail

- Provides governance, compliance and audit for your AWS Account
- CloudTrail is enabled by default.

- Get a history of events / API calls made withing your AWS account by:
    - Console
    - SDK
    - CLI
    - AWS Services
- Can put logs from CloudTrail into CloudWatch Logs or S3
- A trail can be applied to All Regions (default) or a single Region
- If a resource is deleted in AWS, investigate CloudTrail first!

![](img/2022-04-26-18-05-14.png)

The CloudWatch logs and S3 bucket is for the logs we want to keep more than 90 days.

## Events

- Management Events:
    - Operations that are performed on resources in your AWS account
        - Configuring security (IAM AttachRolePolicy)
        - Configuring rules for routing data (AmazonEC2CreateSubnet)
        - Settung up logging (AwsCloudTrailCreateTrail)
    - By default, trails are configured to log management events
    - Can separate ReadEvents (that don't modify resources) from WriteEvents (that may modify resources)
- Data Events
    - By default, data events are not logged (because high volume operations)
    - Amazon S3 object-level activity (ex: GetObject, DeleteObject, PutObject): can separate Read and Write Events
    - AWS Lambda function execution activity (the Invoke API)
- CloudTrail Insights Events

## CloudTrail Insights

- Enable CloudTrail Insights to detect unusual activity in your account:
    - Inaccurate resource provisioning
    - Hitting service limits
    - Bursts of AWS IAM actions
    - Gaps in periodic maintenance activity
- CloudTrail Insights analyzes normal management events to create a baseline
- And then continuously analyzes write events to detect unusual patterns
    - Anomalies appear in the CloudTrail console
    - Event is sent to Amazon S3
    - An EventBridge event is generated for (automation needs)

![](img/2022-04-26-18-10-53.png)

## Events Retention

- Events are stored for 90 days in CloudTrail
- To keep events beyond this period, log them to S3 and use Athena

![](img/2022-04-26-18-11-39.png)