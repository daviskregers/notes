---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cloudwatch, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# CloudWatch Logs

- Applications can send logs to [[CloudWatch]] using the [[AWS SDK]]
- [[CloudWatch]] can collect log from:
    - [[Elastic Beanstalk]]: collection of logs from application
    - [[ECS]]: collection from containers
    - [[AWS Lambda]]: collection from function logs
    - [[VPC Flow logs]]: VPC specific logs
    - [[AWS API Gateway]]
    - [[AWS CloudTrail]] based on filter
    - [[CloudWatch log agent]]s: for example on EC2 machines
    - [[AWS Route 53]]: Log DNS queries
- CloudWatch Logs can go to:
    - Batch exported to [[AWS S3]] archival
    - Stream to [[ElasticSearch]] cluster for further analytics

## AWS CloudWatch Logs

- Logs storage architecture:
    - [[Log groups]]: arbitrary name, usually representing an application
    - [[Log stream]]: instances within application / log files / containers
- Can define log expiration policies (never expire, 30 days, etc)
- Using the [[AWS CLI]] we can tail CloudWatch logs
- To send logs to [[CloudWatch]], make sure [[IAM]] permissions are correct.
- Security: [[Encrpyion]] of logs using [[AWS KMS (Key Management Service)]] at the [[Group Level]]

# CloudWatch Logs Metric Filter & Insights

- CloudWatch Logs can use [[filter expressions]]
    - For example, find a specific IP inside a log
    - Metric filters can be used to trigger alarms

- [[CloudWatch Logs Insights]] (new - Nov 2018) can be used to query logs and add queries to [[CloudWatch Dashboards]].