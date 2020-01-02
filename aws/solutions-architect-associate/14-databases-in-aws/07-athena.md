# Athena

- Fully Serverless database with SQL capabilities
- Used to query data in S3
- Pay per query
- Output results back to S3
- Secured though IAM

---

Use case: one time SQL queries, serverless queries on S3, log analytics

## Athena for Solutions Architect

- **Operations**: no operations needed, serverless
- **Security**: IAM + S3 security
- **Reliability**: managed service, uses Presto engine, highly available
- **Performance**: queries scale based on data size
- **Cost**: pay per query / per TB of data scanned, serverless