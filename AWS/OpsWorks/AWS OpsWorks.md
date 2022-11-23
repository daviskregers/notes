---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/opsworks, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# AWS OpsWorks

- [[Chef]] & [[Puppet]] help you perform [[server configuration]] automatically or repetitive actions
- They work great with [[AWS EC2]] & [[On Premise VM]]
- AWS Opsworks = Managed [[Chef]] & [[Puppet]]
- It's an alternative to [[SSM Parameter Store]]

## Quick word on Chef / Puppet

- They help with managing configuration as code
- Helps in having [[consistent deployments]]
- Works with [[Linux]] / [[Windows]]
- Can automate: user accounts, [[CRON]], [[NTP]], packages, services...
- The leverage "Recipes" or "Manifests"
- [[Chef]] / [[Puppet]] have similarities with [[SSM Parameter Store]] / [[Elastic Beanstalk]] / [[CloudFormation]] but they're open-source tools that work cross-cloud