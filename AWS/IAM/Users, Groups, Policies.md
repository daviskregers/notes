---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-developer-associate-dva-c01
Tags: [development/aws/iam, review]
sr-due: 2023-01-20
sr-interval: 58
sr-ease: 250
---

# IAM introduction: Users, Groups, Policies

- IAM stands for Identity And Access Management
- It is a global service

- [[Root account]] is created by default, shouldn't be used or shared.
- [[IAM user]]s are people within your organization and can be grouped
- [[IAM group]]s can only contain users not other groups. Users can belong to multiple groups though.

- Groups are being created because:
    - You can create [[JSON]] documents called [[IAM Policy]] and assign them to [[IAM group]]s or [[IAM user]]s.
    - These policies define the permissions of the users
    - In AWS you apply the [[least privilege principle]]: don't give more permissions than a user needs.

