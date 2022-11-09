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

## Provisioned Throughput

- Table must have provisioned read and write capacity units
- [[Read Capacity Unit]]s (RCU): throughput for reads ($0.00013 per RCU)
    - 1 RCU = 1 strongly consistent read of 4 KB per second
    - 1 RCU = 2 eventually consistent read of 4 KB per second
- [[Write Capacity Unit]]s (WCU): throughput for writes ($0.00065 per WCU)
    - 1 WCU = 1 write of 1 KB per second
- Option to setup auto-scaling of throughput to meet demand
- Throughput can be exceeded temporarily using "[[burst credit]]"
- If burst credits are empty, you'll get a "[[ProvisionedThoughputException]]"
- It's then advised to do an exponential back-off retry