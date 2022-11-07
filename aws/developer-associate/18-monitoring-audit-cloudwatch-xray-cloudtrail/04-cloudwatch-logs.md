# CloudWatch Logs

- **Log groups** - arbitrary name, usually representing an application
- **Log stream** - instances with application / log files / containers
- Can define lof expiration policies (never expire, 30 days, etc)
- **CloudWatch Logs can send logs to**
    - Amazon S3 (exports)
    - Kinesis Data Streams
    - Kinesis Data Firehose
    - AWS Lambda
    - ElasticSearch

## Sources

- SDK, CloudWatch Logs Agent, CloudWatch Unified Agent
- Elastic Beanstalk: collection of logs from application
- ECS: collection from containers
- AWS Lambda: collection from function logs
- VPC FLow Logs: VPC specific logs
- API Gateway
- CloudTrail based on filter
- Route53: Log DNS queries

## CloudWatch Logs Metric Filter & Insights

- CloudWatch Logs can use filter expressions
    - For example, find a specific IP inside of a log
    - Or count occurences of ERROR in your logs
- Metric filters can be used to trigger CloudWatch alarms
- CloudWatch Logs Insights can be used to query logs and add queries to CloudWatch Dashboards

## S3 Export

- Log data can take up to 12 hours to become available for export
- The API call is CreateExportTask
- Not near-real time or real-time... use Logs Subscriptions instead

## Logs Subscriptions

![](2022-04-26-09-49-56.png)

## Logs Aggregation Multi-Account & Multi Region

![](2022-04-26-09-50-24.png)