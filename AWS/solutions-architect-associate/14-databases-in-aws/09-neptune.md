# Neptune

- Fully managed graph database
- When do we use graphs?
    - High relationship data
    - Social networking: users friends with users, replied to comment on post of user and likes other comments
    - Knowledge graps (wikipedia)
- Highly available accross 3 AZ, with up to 15 read replicas
- Point in time recovery, continuous backup to Amazon S3
- Support for KMS enctyption at rest + HTTPS

## Neptune for Solutions Architect

- **Operations**: Similar to RDS
- **Security**: IAM, VPC, KMS, SSL (similar to RDS) + IAM Authentication
- **Reliability**: Multi-AZ, clustering
- **Performance**: best suited for graphs, clustering to improve performance
- **Cost**: pay per node provisioned (similar to RDS)

---

- Remember - Neptune - graphs