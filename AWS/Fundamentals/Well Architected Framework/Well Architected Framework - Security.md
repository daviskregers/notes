---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals/well-architected-framework, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 230
---

# Second Pillar - Security

- Includes the ability to protect information, systems and assets while delivering business value though [[risk assessment]]s and [[mitigation strategies]]
- Design principles
    - **Implement a string identity foundation** - [[centralise privilege management]] and reduce (or even eliminate) reliance on long-term credentials - [[principe of least privilege]] [[IAM]]
    - **Enable [[traceability]]** - Integrate logs and metrics with systems to automatically respond and take action
    - **Apply security at all layers** - Like [[edge network]], [[VPC]], [[subnet]], [[Load Balancer]], every instance, [[operating system]] and [[application]]
    - **Automate [[security best practices]]**
    - **Protect data in transit and at rest** - [[encryption]], [[tokenization]] and [[access control]]
    - **Keep people away from data** - Reduce or eliminate the need for [[direct access]] or [[manual processing]] of data
    - **Prepare for security events** - run [[incident response simulation]]s and use tools with automation to increase your speed for [[detection]], [[investigation]] and [[recovery]]

- Services
    - [[Identity and Access Management]]
        - [[IAM]]
        - [[AWS STS - Security Token Service]]
        - [[Multi factor authentication]]
        - [[AWS Organizations]]
    - Detective Controls
        - [[AWS Config]]
        - [[CloudTrail]]
        - [[CloudWatch]]
    - Infrastructure Protection
        - [[Programming/AWS/CloudFront/AWS CloudFront]]
        - [[VPC]]
        - [[AWS Shield]]
        - [[AWS WAF]]
        - [[Amazon Inspector]]
    - Data Protection
        - [[AWS KMS (Key Management Service)]]
        - [[AWS S3]]
        - [[Elastic Load Balancer]]
        - [[EBS Volume]]
        - [[RDS Security]]
    - Incident Response
        - [[IAM]]
        - [[CloudFormation]]
        - [[CloudWatch Events]]