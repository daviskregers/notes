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

## Basics

- [[Programming/AWS/DynamoDB/DynamoDB]] is made of tables
- Each table has a [[primary key]] (must be decided at creation time)
- Each table can have an infinite number of items (=rows)
- Each item has attributes (can be added over time - can be null)
- Maximum size of an item is 400KB
- Data types supported are:
    - Scalar types: [[String]], [[Number]], [[Binary]], [[Boolean]], [[Null]]
    - Document types: [[List]], [[Map]]
    - Set types: [[String Set]], [[Number Set]], [[Binary Set]]