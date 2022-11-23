---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/simple-workflow-service, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

## AWS SWF - Simple Workflow Service

- Coordinate work amongst applications
- Code runs on [[AWS EC2]] (not [[serverless]])
- 1 year max runtime
- Concept of "[[activity step]]" and "[[decision step]]"
- Has built-in "[[human intervention]]" step
- Example: order fulfilment from web to warehouse to deliver
- [[AWS Step Functions]] is recommended to be used for new applications except:
    - If you need [[external signals]] to intervene in the [[process]]
    - If you need [[child process]]es that return values to the [[parent process]]es