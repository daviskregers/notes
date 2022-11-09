---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/api-gateway, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## Advanced Features

![[DynamoDB Accelerator (DAX)]]
- [[DynamoDB Streams]]
    - Changes in DynamoDB (Create, Update, Delete) can end up in a DynamoDB stream
    - This stream can be read by [[AWS Lambda]] and we can then do:
        - React to changes in real time (welcome email to new users)
        - Analytics
        - Create derivative tables / views
        - Insert into [[ElasticSearch]]
    - Clould implement cross region replication using Streams
    - Stream has 24 of data retention
- [[Transactions]]
    - All or nothing type of operations
    - Coordinated insert, update, delete across multiple tables
    - Include up to 10 unique items or up to 4MB of data
- On demand
    - No capacity planning needed ([[Write Capacity Unit]]/[[Read Capacity Unit]]) - scales automatically
    - 2.5x more expensive than provisioned capacity (use with care)
    - Helpful when spikes are un-predictable or the application has very low throughput
- Security
    - [[VPC endpoints]] available to access DynamoDB without internet
    - Access fully controlled by [[IAM]]
    - Encryption at rest using [[AWS KMS (Key Management Service)]]
    - Encryption in transit using [[SSL]] / [[TLS]]
- Backup and Restore feature available
    - Point in time restore like [[AWS RDS]]
    - No performance impact
- Global Tables
    - [[Multi region]], fully replication, high performance
- [[Amazon DMS]] can be used to migrate to DynamoDB (from [[MongoDB]], [[Oracle]], [[MySQL]], [[S3]] etc ...)
- You can launch a [[local DynamoDB]] on your computer for development purposes