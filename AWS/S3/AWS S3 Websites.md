---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/s3, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# AWS S3 Websites

- S3 can host static websites and have them accessible on the www
- The website URL will be `<bucket-name>.s3-website-<aws-region>.amazonaws.com` OR `<bucket-name>.s3-website.<aws-region>.amazonaws.com`
- If you get a 403 (forbidden) error, make sure the bucket policy allows public reads.

![](2019-12-30-12-11-32.png)

![](2019-12-30-12-12-26.png)

```json
{
    "Id": "Policy1537533827691",
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Stmt1537533826523",
            "Action": [
                "s3:GetOBject"
            ],
            "Effect": "Allow",
            "Resource": "arm:aws:s3::::thebucket/*",
            "Principal": "*"
        }
    ]
}
```