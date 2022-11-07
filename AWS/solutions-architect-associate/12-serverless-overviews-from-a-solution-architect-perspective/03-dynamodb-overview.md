# DynamoDB

- Fully Managed, Highly available replication accross 3 AZ
- NoSQL database - not a relation database
- Scales to massive workloads, distributed database
- Millions of requests per seconds, trillions of rows, 100s of TB of storage
- Fast and consistend in performance (low latency of retrieval)
- Integrated with IAM for security, authorization and administration
- Enables event driven programming with DynamoDB Streams
- Low cost and autoscaling capabilities

## Basics

- DynamoDB is made of tables
- Each table has a primary key (must be decided at creation time)
- Each table can have an infinite number of items (=rows)
- Each item has attributes (can be added over time - can be null)
- Maximum size of an item is 400KB
- Data types supported are:
    - Scalar types: string, number, binary, boolean, null
    - Document types: list, map
    - Set types: String Set, Number Set, Binary Set

## Privisioned Througput

- Table must have provisioned read and write capacity units
- Read Capacity Units (RCU): throughput for reads ($0.00013 per RCU)
    - 1 RCU = 1 strongly consistend read of 4 KB per second
    - 1 RCU = 2 eventually consistent read of 4 KB per second
- Write Capacity Units (WCU): throughput for writes ($0.00065 per WCU)
    - 1 WCU = 1 write of 1 KB per second
- Option to setup auto-scaling of troughput to meet demand
- Thoutghput can be exceeded temporarily using "burst credit"
- If burst credits are empty, you'll get a "ProvisionedThoughputException"
- It's then advised to do an exponential back-off retry

## Advanced Features

- DAX (DynamoDB Accelerator)
    - Seamless cache for DynamoDB, no application re-write
    - Writes go though DAX to DynamoDB
    - Micro second latency for cached reads & queries
    - Solves the Hot Key problem (too many reads)
    - 5 minutes TTL for cache by default
    - Up to 10 nodes in the cluster
    - Multi AZ (3 nodes minimum recommended for production)
    - Secure (Encryption at rest with KMS, VPC, IAM, CloudTrail)
- DynamoDB Streams
    - Changes in DynamoDB (Create, Update, Delete) can end up in a DynamoDB stream
    - This stream can be read by AWS Lamda and we can then do:
        - React to changes in real time (welcome email to new users)
        - Analytics
        - Create derivative tables / views
        - Insert into ElasticSearch
    - Clould implement cross reguin replication using Streams
    - Stream has 24 of data retention
- Transactions
    - All or nothing type of operations
    - Coordinated insert, update, delete accross multiple tables
    - Include up to 10 unique items or up to 4MB of data
- On demand
    - No capacity planning needed (WCU/RCU)- scales automatically
    - 2.5x more expensive than provisioned capacity (use with care)
    - Helpful when spikes are un-predictable or the application has very low thoughput
- Security
    - VPC Endpoints available to access DynamoDB without internet
    - Access fully controlled by IAM
    - Encryption at rest using KMS
    - Encryption in transit using SSL / TLS
- Backup and Restore feature available
    - Point in time restore like RDS
    - No performance impact
- Global Tables
    - Multi region, fully replication, high performance
- Amazon DMS can be used to migrate to DynamoDB (from Mongo, Oracle, Mysql, S3 etc ...)
- You can launch a local DynamoDB on your computer for development purposes