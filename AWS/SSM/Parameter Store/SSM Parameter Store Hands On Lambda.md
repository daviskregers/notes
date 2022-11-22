---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ssm/parameter-store, review]
sr-due: 2022-12-16
sr-interval: 24
sr-ease: 250
---

# SSM Parameter Store Hands On Lambda

Create a new [[AWS Lambda]] function

![](2020-01-01-14-52-53.png)

Insert code:

```python
import json
import boto3

ssm = boto3.client('ssm', region_name="eu-west-1")

def lambda_handler(event, context):
    db_url = ssm.get_parameters(Names=['/my-app/dev/db-url'])
    print(db_url)
    db_password = ssm.get_parameters(Names=['/my-app/dev/db-password'], WithDecryption=True)
    print(db_password)
```

When testing, we are going to get an error:

```
An error occurred (AccessDeniedException) when calling the GetParameters operation: User: arn:aws:sts::539690530154:assumed-role/hello-world-ssm-role-ta2hmdtc/hello-world-ssm is not authorized to perform: ssm:GetParameters on resource: arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-url
```

We are going to open up the [[AWS Lambda]] role and `Add Inline Policy`:

![](2020-01-01-14-59-28.png)

![](2020-01-01-15-01-30.png)

![](2020-01-01-15-02-00.png)

Now if we test, we get:

```
An error occurred (AccessDeniedException) when calling the GetParameters operation: The ciphertext refers to a customer master key that does not exist, does not exist in this region, or you are not allowed to access. (Service: AWSKMS; Status Code: 400; Error Code: AccessDeniedException; Request ID: 59647aab-d88f-4bf5-8ac7-b358b03f4722)
```

We are going to add one more [[inline policy]]:

![](2020-01-01-15-07-14.png)

Now, when testing, we get

```json
START RequestId: 80755a69-a761-4fe2-832b-3148a123e8be Version: $LATEST
{'Parameters': [{'Name': '/my-app/dev/db-url', 'Type': 'String', 'Value': 'dev.db.domain.com', 'Version': 1, 'LastModifiedDate': datetime.datetime(2020, 1, 1, 12, 45, 35, 442000, tzinfo=tzlocal()), 'ARN': 'arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-url'}], 'InvalidParameters': [], 'ResponseMetadata': {'RequestId': 'fcf16f9e-fce5-4e4c-a98d-80bf5ce6299a', 'HTTPStatusCode': 200, 'HTTPHeaders': {'x-amzn-requestid': 'fcf16f9e-fce5-4e4c-a98d-80bf5ce6299a', 'content-type': 'application/x-amz-json-1.1', 'content-length': '250', 'date': 'Wed, 01 Jan 2020 13:07:22 GMT'}, 'RetryAttempts': 0}}
{'Parameters': [{'Name': '/my-app/dev/db-password', 'Type': 'SecureString', 'Value': 'mysupersecretdevpassword', 'Version': 1, 'LastModifiedDate': datetime.datetime(2020, 1, 1, 12, 46, 24, 389000, tzinfo=tzlocal()), 'ARN': 'arn:aws:ssm:eu-west-1:539690530154:parameter/my-app/dev/db-password'}], 'InvalidParameters': [], 'ResponseMetadata': {'RequestId': '95d2f060-3fe5-413e-94eb-5de5f16542b7', 'HTTPStatusCode': 200, 'HTTPHeaders': {'x-amzn-requestid': '95d2f060-3fe5-413e-94eb-5de5f16542b7', 'content-type': 'application/x-amz-json-1.1', 'content-length': '273', 'date': 'Wed, 01 Jan 2020 13:07:22 GMT'}, 'RetryAttempts': 0}}
it works!
END RequestId: 80755a69-a761-4fe2-832b-3148a123e8be
REPORT RequestId: 80755a69-a761-4fe2-832b-3148a123e8be	Duration: 243.28 ms	Billed Duration: 300 ms	Memory Size: 128 MB	Max Memory Used: 79 MB	
```