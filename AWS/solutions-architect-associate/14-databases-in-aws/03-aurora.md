# Aurora

- Compatible API for PostgreSQL / MySQL
- Data is help in 6 replicas, accross 3 AZ
- Auto healing capability
- Multi AZ, Auto Scaling Read Replicas
- Read Replicas can be Global
- Aurora database can be Global for DR or latency purposes
- Auto scaling of storage from 10GB to 64 TB
- Define EC2 instance type for aurora instances
- Same security / monitoring / maintenance features as RDS
- Aurora serverless option

---

Use case: same as RDS, but with less maintenance / more flexibility / more performance

## Aurora for Solutions Architect

- **Operations**: less operations, auto scaling storage
- **Security**: AWS responsible for OS security, we are responsible for setting up KMS, security groups, IAM policies, authorizing users in DB, using SSL
- **Reliability**: Multi AZ, highly available, possibly more than RDS, Aurora Serverless option.
- **Performance**: 5x performance (according to AWS) due to architectural optimizations. Up to 15 Read replicas (only 5 for RDS)
- **Cost**: Pay per hour based on EC2 and storage usage. Possibly lower costs compared to Enterprise grade databases such as Oracle.