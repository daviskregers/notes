---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS S3 - Consistency model

- Read after write consistency for [[HTTP PUT]]S of new objects
    - As soon as an object is written, we can retrieve it ([[HTTP PUT]] 200 -> [[HTTP GET]] 200)
    - This is true, except if we did a GET before to see if the object existed ([[HTTP GET]] 404 -> [[HTTP PUT]] 200 -> [[HTTP GET]] 404) - eventually consistent
- Eventual Consistency for [[HTTP DELETE]]S and PUTS of existing objects
    - If we read an object after updating, we might get the older version
    - If we delete an object, we might still be able to retrieve it for a short time