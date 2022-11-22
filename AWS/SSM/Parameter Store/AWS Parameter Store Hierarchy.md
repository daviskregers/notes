---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ssm/parameter-store, review]
sr-due: 2023-01-18
sr-interval: 57
sr-ease: 270
---

## AWS Parameter Store Hierarchy

- /my-departments
    - my-app/
        - dev/
            - db-url
            - db-password
        - prod/
            - db-url
            - db-password
    - other-app/
- other-department

use with `GetParameters` or `GetParametersByPath` API in [[AWS Lambda]] functions.

