---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3/tiers, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

## S3 Lifecycle Rules

- Set rules to move data between different tiers to save storage cost
- Example: [[S3 Standard Tier (General Purpose)]] => [[S3 Standard-Infrequent Access (IA) Tier]] => [[S3 Glacier]]

- Transition actions: It defines when objects are transitioned to another [[storage class]].
    - Eg: We can choose to move [[AWS S3 Objects]] to [[S3 Standard-Infrequent Access (IA) Tier]] class 60 days after you created them or can move to [[S3 Glacier]] for archiving after 6 months

- Expiration actions: Helps to configure objects to expire after a certain time period. S3 deletes expired [[AWS S3 Objects]] on our behalf
    - Eg: [[S3 Access logs]] files can be set to delete after a specified period of time

- Can be used to delete incomplete [[multi-part uploads]]

![](2019-12-31-08-48-24.png)

![](2019-12-31-08-50-11.png)

![](2019-12-31-08-51-04.png)