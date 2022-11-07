# Exponential Backoff & Service Limit Increase

## AWS Limits (Quotas)

- API Rate Limits
    - DescribeInstances API for EC2 has a limit of 100 calls per second
    - GetObject on S3 has a limit of 5500 GET per second per prefix
    - For Intermittent Errors: implement Exponential backoff
    - For Consistent Errors: request an API throttling limit increase
- Service Quotas (Service Limits)
    - Running On-Demand Standard Instances: 1152 vCPU
    - You can request a service limit increase by opening a ticket
    - You can request quote increase by using Service Quotas API

## Exponential Backoff (any AWS Service)

- If you get ThrottlingException intermittently, use exponential backoff
- Retry mechanism already included in AWS SDK API calls
- Must implement yourself if using the AWS API as-is or in specific cases
    - Must only implement retries on 5xx server errors and throttling
    - Do not implement on 4xx client errors