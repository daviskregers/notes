# Redshift

- Redshift is based on PostgreSQL, but it's not used for OLTP
- It's OLAP - online analytical processing (analytics and data warehousing)
- 10x better performance than other data warehouses, scale to PBs of data
- Massively Parralel Query Execution (MPP), highly available
- Pay as you go based on the instances provisioned
- Has a SQL interface for performing the queries
- BI tools such as AWS Quicksight or Tableau integrate with it

- Data is loaded from S3, DynamoDB, DMS, other DBs
- From 1 node to 128 nodes, up to 160GB of space for node
- Leader node: for query planning, results aggregation
- Compute node: for performing the queries, send results to leader
- Redshift Spectrum: perform queries directly against S3 (no need to load)
- Backup & Restore, Security VPC / IAM / KMS, Monitoring
- Redshift Enhanced VPC Routing: COPY / UNLOAD goes through VPC

## Redshift for Solutions Architect

- **Operations**: similar to RDS
- **Security**: IAM, VPC, KMS, SSL (similar to RDS)
- **Reliability**: highly available, auto healing features
- **Performance**: 10x performance vs other data warehousing, compression
- **Cost**: pay per node provisioned, 1/10th of the cost vs other warehouses

---

Remember: Redshift = analytics / BI / Data warehouse