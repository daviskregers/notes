# S3 Storage Classess

- Amazon S3 Standard - General Purpose
- Amazon S3 Standard-Infrequent Access (IA)
- Amazon S3 One Zone-Infrequent Access
- Amazon S3 Intelligent Tiering
- Amazon Glacier
- Amazon Glacier Deep Archive
- Amazon S3 Reduced Redundancy Storage

## Amazon S3 Standard - General Purpose

- High durability (99.99999999999%) of objects across multiple AZ
- If you store 10,000,000 objects with Amazon S3, you can on average expect to incur a loss of a single object once every 10,000 years
- 99.99% availability over a given year
- Sustain 2 concurrent facility failures

- Use Cases: Big Data analytics, mobile & haming applications, content distribution...

## Amazon S3 Standard - Infrequent Access (IA)

- Suitable for data that is less frequently accessed, but requires rapid access when needed
- High durability (99.99999999999%) of objects across multiple AZs
- 99.99% availability
- Low cost compared to Amazon S3 Standard
- Sustain 2 concurrent facility failures

- Use cases: As a data store for disaster recovery, backups

## Amazon S3 One Zone - Infrequent Access (IA)

- Same as IA but data is stored in a single AZ
- High durability (99.99999999999%) of objects ub a single AZ, data lost when AZ is destroyed
- 99.5% Availability
- Low latency and high throughput performance
- Supports SLL for data at transit and encryption at rest
- Low cost compared to IA (by 20%)
- Use Cases: Storing secondary beckup copies of on-premise data, or storing data you can recreate.

## Amazon S3 Intelligent Tiering

- Same low latency and high throughput performance of S3 Standard
- Small monthly monitoring and auto-tiering fee
- Automatically moves objects between two access tiers based on changing access patterns
- Designed for durability of 99.99999999999% of objects across multiple availability zones
- Reslilient against events that impact an entire Availability Zone
- Designed for 99.9% availability over a given year

## Amazon S3 Glacier

- Low cost object storage meant for archiving / backups
- Data is retained for the longer term (10s of years)
- Alternative to on-premise magnetic tape storage
- Average anual durability is 99.99999999999%
- Cost per storage per month ($0.004 / GB) + retrieval cost
- Each item in Glacier is called "Archive" (up to 40TB)
- Archives are stored in "Vaults"

## Amazon Glacier & Glacier Deep Archive

- Amazon Glacier - 3 retrieval options:
    - Expedited (1 to 5 minutes)
    - Standard (3 to 5 hours)
    - Bulk (5 to 12 hours)
    - Minimum storage duration of 90 days

- Amazon Glacier Deep Archive - for long term storage - cheaper
    - Standard (12 hours)
    - Bulk (48 hours)
    - Minimum storage duration of 180 days

## S3 Storage Classes Comparison

We can see the comparison of the classes here: https://aws.amazon.com/s3/storage-classes/