---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/lambda, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## AWS Lamda Limits

- Execution
    - [[Memory]] allocation: 128MB to 3008MB (64MB increments)
    - Maximum [[execution time]]: 15 minutes
    - Disk capacity in the "function container" (in /tmp): 512MB
    - [[Concurrency]] limits: 1000 (no of functions that can concurrently execute)
        - Can be increased by writing a support ticket.
- Deployment 
    - [[AWS Lambda]] function deployment size (compressed .zip): 50MB
    - Size of uncompressed deployment (code + dependencies): 250 MB
    - Can use the /tmp directory to load other files at startup
    - Size of [[environment variables]]: 4KB