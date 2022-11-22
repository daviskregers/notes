---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ssm/parameter-store, review]
sr-due: 2022-12-14
sr-interval: 22
sr-ease: 250
---

# SSM Parameter Store hands on CLI

We can search for [[Systems Manager]] in [[AWS Console]] and then navigate to [[SSM Parameter Store]] section.

And add params:

![](2020-01-01-14-45-31.png)

![](2020-01-01-14-46-19.png)

![](2020-01-01-14-47-58.png)

Then query via [[AWS CLI]]

```json
➜  ~ aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password
{
    "Parameters": [
        {
            "Name": "/my-app/dev/db-password",
            "Type": "SecureString",
            "Value": "AQICAHhSgKv4yUSMN7xTX6TV5+owFLPqV7u3thrIPV83oQBh6AGQBrWbtKy9FhfLFZmp1aBlAAAAdjB0BgkqhkiG9w0BBwagZzBlAgEAMGAGCSqGSIb3DQEHATAeBglghkgBZQMEAS4wEQQMRUzwDLakNxxfAoZLAgEQgDMt5tCgJphvuAtDng+Lhuas/aaR0ecOpy42PGq7uK5Fxik8routwmNgIT/2H0ubJiAkhuY=",
            "Version": 1,
            "LastModifiedDate": 1577882784.389,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-password"
        },
        {
            "Name": "/my-app/dev/db-url",
            "Type": "String",
            "Value": "dev.db.domain.com",
            "Version": 1,
            "LastModifiedDate": 1577882735.442,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-url"
        }
    ],
    "InvalidParameters": []
}
```

Decrypt password:

```json
➜  ~ aws ssm get-parameters --names /my-app/dev/db-url /my-app/dev/db-password --with-decryption
{
    "Parameters": [
        {
            "Name": "/my-app/dev/db-password",
            "Type": "SecureString",
            "Value": "mysupersecretdevpassword",
            "Version": 1,
            "LastModifiedDate": 1577882784.389,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-password"
        },
        {
            "Name": "/my-app/dev/db-url",
            "Type": "String",
            "Value": "dev.db.domain.com",
            "Version": 1,
            "LastModifiedDate": 1577882735.442,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-url"
        }
    ],
    "InvalidParameters": []
}
```

Via path query:

```json
➜  ~ aws ssm get-parameters-by-path --path /my-app/ --recursive --with-decryption
{
    "Parameters": [
        {
            "Name": "/my-app/dev/db-password",
            "Type": "SecureString",
            "Value": "mysupersecretdevpassword",
            "Version": 1,
            "LastModifiedDate": 1577882784.389,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-password"
        },
        {
            "Name": "/my-app/dev/db-url",
            "Type": "String",
            "Value": "dev.db.domain.com",
            "Version": 1,
            "LastModifiedDate": 1577882735.442,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-url"
        },
        {
            "Name": "/my-app/prod/db-password",
            "Type": "SecureString",
            "Value": "mysupersecretprodpassword",
            "Version": 1,
            "LastModifiedDate": 1577882871.1,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/prod/db-password"
        },
        {
            "Name": "/my-app/prod/db-url",
            "Type": "String",
            "Value": "prod.db.domain.com",
            "Version": 1,
            "LastModifiedDate": 1577882848.24,
            "ARN": "arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/prod/db-url"
        }
    ]
}
```