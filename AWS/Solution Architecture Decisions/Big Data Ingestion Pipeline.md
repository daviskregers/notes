---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Big Data Ingestion Pipeline

- We want the ingestion pipeline to be fully [[serverless]]
- We want to collect data in real time
- We want to transform the data
- We want to query the transformed data using [[SQL]]
- The reports created using the queries should be in [[AWS S3]]
- We want to load that data into a [[Data warehouse]] and create [[dashboards]]

![](2020-01-01-12-36-11.png)

- [[IoT core]] allows you to harvest data from [[IoT device]]s
- [[Kinesis]] is great for [[real-time data collection]]
- [[Kinesis Firehose]] helps with data delivery to [[AWS S3]] in near real-time (1 minute)
- Lambda can help [[Kinesis Firehose]] with [[data transformations]]
- [[AWS S3]] can trigger notifications to [[AWS SQS]]
- [[AWS Lambda]] can subscribe to [[AWS SQS]] (we could have connected [[AWS S3]] to [[AWS Lambda]])
- [[AWS Athena]] is a [[serverless]] [[SQL]] service and results are stored in [[AWS S3]]
- The reporting [[AWS S3 Bucket]] contains analysed data and can be used by reporting tool such as [[AWS QuickSight]], [[~ Inbox/Redshift]] etc.

