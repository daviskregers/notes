# Athena Overview

- Serverless query service to perform analytics against S3 objects
- Uses standard SQL language to query the files
- Supports CSV, JSON, ORC, Avro and Parquet
- Pricing: $5.00 per TB of data scanned
- Use compressed or columnar data for cost-savings (less scan)
- Use cases: Business Intelligence / analytics / reporting, analyze & query FPC Flow logs, ELB logs, CloudTrail trails etc...

Exam Tip: Analyze data in S3 using serverless SQL, use athena.

Users -- load data --> S3 Bucket -- query & analyze --> Athena -- Reporting & Dashboards --> Amazon QuickSight