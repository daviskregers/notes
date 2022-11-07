---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/rds, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# RDS Hands on

We can go to the `RDS section` in AWS. And click on `create a database`. We are going to use `Standard Create` and `MySQL` because the aurora does not provide free tier.

Then we need:
- Set a template (production, dev/test/free tier)
- Specify identifier
- Specify admin credentials
- Choose instance type
- Specify storage
- Choose whether to use Multi-AZ deployment
- Choose the VPC to deploy to, security groups, publicly accessable?
- Setup additional configuration
    - Backups
    - Monitoring
    - Logging
    - Maintenance
    - Deletion prevention

Normally we wouldn't want for the Database to be publicly accessible, but we are going to select it for testing purposes.

![](2019-12-30-08-51-04.png)

Once everything is set up, the instance will need a few minutes to deploy.

![](2019-12-30-08-51-42.png)

Once that is done, we can grab the endpoint URL and connect to it:

![](2019-12-30-08-55-46.png)

When opening up the database section, we can see all the configuration, monitoring dashboards etc.

![](2019-12-30-08-59-40.png)

We can also take multiple actions like delete database, upgrade it, create replicas or snapshots, migrate them to other regions.

![](2019-12-30-09-00-16.png)