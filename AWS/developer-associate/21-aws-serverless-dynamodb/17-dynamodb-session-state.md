# DynamoDB as Session State Cache

- It's common to use DynamoDB to store session state
- vs ElastiCache:
    - ElastiCache is in-memory, but DynamoDB is serverless
    - Both are key/value stores
- vs EFS
    - EFS must be attached to EC2 instances as a network drive
- vs EBS & Instance Store
    - EBS & Instance Store can only be used for local caching, not shared caching
- vs S3:
    - S3 is higher latency, and not meant for small objects