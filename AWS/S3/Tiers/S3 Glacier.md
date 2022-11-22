---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/tiers, review]
sr-due: 2023-01-15
sr-interval: 54
sr-ease: 270
---

# Amazon Glacier

- Low cost object storage meant for [[archiving]] / [[backup]]s
- Data is retained for the longer term (10s of years)
- Alternative to on-premise [[magnetic tape storage]]
- Average to annual durability is 99.999999999%
- Cost per storage per month ($0.004 / GB) + retrieval cost
- Each item in Glacier is called "Archive" (up to 40TB)
- Archives are stored in "Vaults"
- 3 retrieval options:
	- Expedited (1 to 5 minutes retrieval) - $0.04 per GB and $0.01 per request
	- Standard (3 to 5 hours) - $0.01 per GB and 0.05 per 1000 requests
	- Bulk (5 to 12 hours) - $0.0025 per GB and $0.025 per 1000 requests