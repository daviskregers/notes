---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/iam, review]
sr-due: 2022-12-01
sr-interval: 14
sr-ease: 250
---

# IAM Introduction

- IAM stands for Identity and Access Management
- Your whole AWS security is there:
    - Users
    - Groups
    - Roles
- Root account should never be used (and shared)
- Users must be created with proper permissions
- IAM is at the center of AWS
- Policies are written in [[JSON]]

![](../../../images/2019-11-22-10-04-04.png)

- IAM has a **global** view
- [[Multi factor authentication]] can be setup
- IAM has predefined "managed policies"
- It's best to give users the minimal amount of permissions they need to perform their job ([[least privilege principle]])

![[IAM Federation]]

![[Programming/AWS/IAM/IAM Best Practices]]

[[ IAM Hands On]]
