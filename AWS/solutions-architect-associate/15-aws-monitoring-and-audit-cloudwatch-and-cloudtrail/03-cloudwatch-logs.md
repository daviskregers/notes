# CloudWatch Logs

- Applications can send logs to CloudWatch using the SDk
- CloudWatch can collect log from:
    - Elastic Beanstalk: collection of logs from application
    - ECS: collection from containers
    - AWS Lambda: collection from function logs
    - VPC Flow logs: VPC specific logs
    - API Gateway
    - CloudTrail based on filter
    - CloudWatch log agents: for example on EC2 machines
    - Route53: Log DNS queries
- CloudWatch Logs can go to:
    - Batch exported to S3 archival
    - Stream to ElasticSearch cluster for further analytics

## AWS CloudWatch Logs

- Logs storage architecture:
    - Log groups: arbitrary name, usually representing an application
    - Log stream: instances within application / log files / containers
- Can define log expiration policies (never expire, 30 days, etc)
- Using the AWS CLI we can tail CloudWatch logs
- To send logs to CloudWatch, make sure IAM permissions are correct.
- Security: Encryption of logs using KMS at the Group Level

# CloudWatch Logs Metric Filter & Insights

- CloudWatch Logs can use filter expressions
    - For example, find a specifi IP inside a log
    - Metric filters can be used to trigger alarms
- CloudWatch Logs Insights (new - Nov 2018) can be used to query logs and add queries to CloudWatch Dashboards.