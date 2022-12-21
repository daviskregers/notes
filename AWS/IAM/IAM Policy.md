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

# IAM Policy

We can have [[IAM group]] that contain people. If we attach policies to those groups, all the users will receive these permissions.
[[IAM user]]s can be in multiple groups.

There is an option to attach an [[Inline policy]] as well. In this case the policy is attached directly to a user.

## IAM Policies Structure

- Consists of
    - Version: policy language version, always include "2012-10-17"
    - Id: an identifier for the policy (optional)
    - Statement: one or more individual statements (required)
- Statements consist of
    - Sid: an identifier for the statement (optional)
    - Effect: whether the statement allows or denies access (Allow, Deny)
    - Action: list of actions this policy allows or denies
    - Resource: list of resources to which the actions applied to
    - Condition: conditions for when this policy is in effect (optional)

```json
{
    "Version": "2012-10-17",
    "Id": "S3-Account-Permissions",
    "Statement": [
        {
            "Sid": "1",
            "Effect": "Allow",
            "Principal": {
                "AWS" ["arn:aws:iam:123456789012:root"]
            },
            "Action": ]
                "s3:GetObject",
                "s3:PutObject"
            ],
            "Resource": ["arn:aws:s3:::mybucket/*"]
        }
    ]
}
```
