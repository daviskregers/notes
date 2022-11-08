---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cli, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS CLI on [[AWS EC2]]

## AWS CLI ON EC2 - The bad way

- We could run `aws configure` on EC2 just like we did (and it will work)
- But it's insecure
- never put your personal credentials on an EC2
- Your personal credentials only belong on your personal computer

- If the EC2 is compromised, so is your personal account
- If the EC2 is shared, other people may perform AWS actions while impersonating you

- For EC2, there's a better way. It's called [[IAM Role]]

## The right way

- [[IAM Role]] can be attached to [[AWS EC2]] Instances
- IAM Roles can come with a policy authorizing exactly what the ec2 instance should be able to do
- EC2 Instances can then use these profiles automatically without any additional confurations
- *This is the best practice on AWS and you should 100% do this.*

In order to do this, we go to `IAM` service and create a new role, attach it to an EC2 service, attach policies that we need.

![](2019-12-30-12-41-43.png)