---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals/well-architected-framework, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 210
---

# Third Pillar - Reliability

- Ability of a system to recover from [[infrastructure]] or [[service]] [[disruption]]s, dynamically acquire computing resources to meet demand, and mitigate disruptions such as misconfigurations or transient network issues
- Design principles
    - **Test [[recovery procedure]]s** - Use automation to simulate different failures or to **recreate scenarios that led to failures before**
    - **Automatically recover from failure** - Anticipate and remediate failures before they occur
    - **Scale horizontally to increase aggregate system availability** - Distribute requests across multiple, smaller resources to ensure that they don't share a common point of failure
    - **Stop guessing capacity** - Maintain the optimal level to satisfy demand without over under provisioning - Use [[Auto Scaling]]
    - **Manage change in automation** - Use automation to make changes to infrastructure
- AWS Services
    - Foundations
        - [[IAM]]
        - [[VPC]]
        - [[Service Limits]]
        - [[AWS Trusted Advisor]]
    - Change Management
        - [[Auto Scaling]]
        - [[CloudWatch]]
        - [[CloudTrail]]
        - [[AWS Config]]
    - Failure Management
        - [[Backups]]
        - [[CloudFormation]]
        - [[AWS S3]]
        - [[S3 Glacier]]
        - [[AWS Route 53]]