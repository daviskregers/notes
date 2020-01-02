# ElastiCache

- Managed Redis / Memcached (similar offering as RDS, but for caches)
- In-memory data store, sub-millisecond latency
- Must provision an EC2 instance type
- Support for Clustering (Redis) and Multi AZ, Read Replicas (sharding)
- Security though IAM, Security Groups, KMS, Redis Auth
- Backup / Snapshot / Point in time restore feature
- Managed and Scheduled maintenance
- Monitoring though CloudWatch

---

- Use case: key/value store, frequent reads, less writes, cache results for DB queries, store session data for websites, cannot use SQL.

## ElastiCache for Solutions Architect

- **Operations**: same as RDS
- **Security**: AWS responsible for OS security, we are responsible for setting up KMS, security groups, IAM policies, users (Redis Auth), using SSL
- **Reliability**: Clustering, Multi AZ
- **Performance**: Sub-millisecond performance, in memory, read replicas for sharding, very popular cache option
- **Cost**: Pay per hour based on EC2 and storage use