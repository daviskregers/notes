---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/kinesis, review]
sr-due: 2022-12-17
sr-interval: 25
sr-ease: 250
---

# Kinesis

- Kinesis is a managed alternative to [[Apache Kafka]]
- Great for allocation logs, metrics, IoT, clickstreams
- Great for "real-time" [[big data]]
- Great for streaming processing frameworks ([[Spark]], [[NiFi]], etc...)
- Data is automatically replicated to 3 [[Availability Zone]]s

- [[Kinesis Streams]]: low latency streaming ingest at scale
- [[Kinesis Analytics]]: perform real-time analytics on streams using SQL
- [[Kinesis Firehose]]: load streams into [[S3]], [[~ Inbox/Redshift]], [[ElasticSearch]]...

## Kinesis overview

- Streams are divided in ordered Shards / Partitions (like ordered queue)
- Data retention is 1 day by default, can go up to 7 days
- Ability to reprocess / replay data
- Multiple applications can consume the same stream
- Real-time processing with scale of throughput
- Once data inserted in Kinesis, it can't be deleted ([[immutability]])

![[Kinesis Streams Shards]]

![[AWS Kinesis API - Put Records]]

![[AWS Kinesis API - Exceptions]]

![[AWS Kinesis - Consumers]]

[[ Kinesis Hands On ]]

![[Kinesis Security]]

![[Kinesis Data Analytics ]]

![[ Kinesis Firehose]]