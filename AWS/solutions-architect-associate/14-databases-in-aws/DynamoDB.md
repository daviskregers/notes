# DynamoDB

- AWS proprietary technology, managed NoSQL database
- Serverless, provisioned capacity, auto scaling, on demand capacity (Nov 2018)
- Can replace ElastiCache as a key/value store (storing session data for example)
- Highly Available, Multi AZ by default, Read and Writes are decoupled, DAX for read cache
- Reads can be eventually consistent or strongly consistent
- Security, authentication and authorization is done though IAM
- DynamoDB Streams to integrate with AWS Lamda
- Backup / Restore feature, Global Table feature
- Monitoring though CloudWatch
- Can only query on primary key, sort key, or indexes

---

Use case: Serverless applications development (small dovuments 100s KB), distributed serverless cache, doesn't have SQL query language available, has transactions capability from Nov 2018.

## DynamoDB for Solutions Architect

- **Operations**: no operations needed, auto scaling capability, serverless
- **Security**: full security though IAM policies, KMS encryption, SSL in flight
- **Reliability**: Multi AZ, Backups
- **Performance**: Single digit millisecond performance, DAX for caching reads, performance doesn't degrade if your application scales
- **Cost**: Pay per provisioned capacity and storage usage (no need to guess in advance any capacity - can use auto scaling)

