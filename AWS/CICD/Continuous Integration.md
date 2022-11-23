---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cicd, networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# Continuous Integration

- Developers push the code to a [[code repository]] often ([[Github]] / [[CodeCommit]] / [[Bitbucket]] / etc)
- A testing / build server checks the code as soon as it's pushed ([[CodeBuild]] / [[Jenkins CI]] / etc)
- The developer gets feedback about the tests and checks that have passed / failed
- [[Find bugs]] early, [[fix bugs]]
- [[Deliver]] faster as the code is tested
- [[Deploy]] often
- Happier developers as they're unblocked

![](2020-01-02-14-18-39.png)

---

- Ensure that the software can be released reliably whenever needed
- Ensures deployments happen often and are quick
- Shift away from "on release every 3 months" to "5 releases a day"
- That usually means automated deployment
    - [[CodeDeploy]]
    - [[Jekins CD]]
    - [[Spinnaker]]
    - Etc

![](2020-01-02-14-20-17.png)