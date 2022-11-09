---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/api-gateway, database, serverless, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# DynamoDB

- [[Fully Managed]], [[Highly available]] [[replication]] across 3 [[Availability Zone]]s
- [[NoSQL database]] - not a [[relation database]]
- Scales to massive workloads, [[distributed database]]
- Millions of requests per seconds, trillions of rows, 100s of TB of storage
- Fast and consistent in performance (low latency of retrieval)
- Integrated with [[IAM]] for security, authorization and administration
- Enables event driven programming with [[DynamoDB Streams]]
- Low cost and autoscaling capabilities

- AWS proprietary technology, managed [[NoSQL]] database
- [[Serverless]], [[provisioned capacity]], [[auto scaling]], [[on demand capacity]] (Nov 2018)
- Can replace [[ElastiCache]] as a [[key-value store]] (storing session data for example)
- [[Highly Available]], [[Multi AZ]] by default, [[Read and Writes are decoupled]], [[DAX (DynamoDB Accelerator)]] for read [[cache]]
- Reads can be [[eventually consistent]] or [[strongly consistent]]
- Security, authentication and authorization is done though [[IAM]]
- [[DynamoDB Streams]] to integrate with [[AWS Lambda]]
- Backup / Restore feature, Global Table feature
- [[Monitoring]] though [[CloudWatch]]
- Can only query on [[primary key]], [[sort key]], or [[indexes]]

---

Use case: [[Serverless]] applications development (small documents 100s KB), distributed serverless cache, doesn't have [[SQL]] query language available, has [[transactions]] capability from Nov 2018.

![[DynamoDB for Solutions Architect]]



![[DynamoDB Basics]]

![[DynamoDB Provisioned Throughput]]

![[DynamoDB Advanced Features]]






