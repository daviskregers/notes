# RDS

- Managed PostgreSQL / MySQL / Oracle / SQL Server
- Must provision an EC2 instance & EBS VOlume type and size
- Support for Read REplicas and Multi AZ
- Security through IAM, Security Groups, KMS, SSL in transit
- Backup / Snapshot / Point in time restore feature
- Managed and Scheduled maintenance
- Monitoring though CloudWatch

---

- Use case: store relational datasets (RDBMS/OLTP), perform queries, transactional inserts / update / delete is available.

## RDS for Solutions Architect

- **Operations**: small downtime when failover happens, when maintenance happens, scaling in read replicas / ec2 instance / restore EBS implies manual intervention, application changes
- **Security**: AWS responsible for OS security, we are responsible for setting up KMS, security groups, IAM policies, authorizing users in DB, using SSL
- **Reliability**: Multi AZ feature, failover in case of failures
- **Performance**: depends on EC2 instance type, EBS volume type, ability to add read replicas. Doesn't auto-scale
- **Cost**: Pay per hour based on provisioned EC2 and EBS
