# Kinesis Client Library (KCL)

- A java library that helps read record from a Kinesis Data Stream with distributed applications sharing the read workload
- Each shard is to be read by only one KCL instance
    - 4 shards = max 4 KCL instances
    - 6 shards = max 6 KCL instances
- Progress is checkpointed into DynamoDB (needs IAM access)
- Track other workers and share the work amongst shards using DynamoDB
- KCL can run on EC2, ElasticBeanstalk, and on premises
- Records are read in order at the shard level
- Versions:
    - KCL 1.x (supports shared consumer)
    - KCL 2.x (supports shared consumer & enhanced fan-out consumer)

