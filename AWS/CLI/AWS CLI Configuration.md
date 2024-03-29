---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/cli, review]
sr-due: 2023-01-10
sr-interval: 49
sr-ease: 250
---

# [[AWS CLI]] Configuration

In order to configure [[AWS CLI]] we need to get access credentials from [[IAM]]. It will be located under `Users -> {user} -> Security Credentials -> Access Keys`.

Then we are going to run

```
➜  ~ aws --version
aws-cli/1.16.303 Python/3.8.0 Linux/5.4.2-arch1-1 botocore/1.13.39
➜  ~ aws configure
AWS Access Key ID [None]: XXX
AWS Secret Access Key [None]: XXXX
Default region name [None]: eu-west-1
Default output format [None]: 
➜  ~ aws configure
AWS Access Key ID [****************XXXX]: 
AWS Secret Access Key [****************XXXX]: 
Default region name [eu-west-1]: 
Default output format [None]: 
➜  ~ ls ~/.aws
config  credentials
➜  ~ cat ~/.aws/config 
[default]
region = eu-west-1

```


For configuring CLI on EC2 - there's a good way and a bad way. Look into [[AWS CLI on EC2]].