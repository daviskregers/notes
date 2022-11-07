# Lambda and CloudFormation

## Inline

- Inline functions are very simple
- Use the Code.ZipFile property
- You cannot include function dependencies with inline functions

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Lambda function inline
Resources:
    primer:
        Type: AWS::Lambda::Function
        Properties:
            Runtime: python3.x
            Role: arn:aws:iam:...:role/lambda-role
            Handler: index.handler
            Code:
                ZipFile: |
                import os

                DB_URL = os.getenv("DB_URL")
                db_client = db.connect(DB_URL)
                def handler(event, context):
                    return db_client.get(user_id = event["user_id"])
```

## Through S3

- You must store the Lambda zip in S3
- You must refer the S3 zip location in the CloudFormation code
    - S3 Bucket
    - S3Key: full path to zip
    - S3ObjectVersion: if versioned bucket
- If you update the code in S3, but don't update S3Bucket, S3Key or S3ObjectVersion, CloudFormation won't update your function.

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Lambda function inline
Resources:
    primer:
        Type: AWS::Lambda::Function
        Properties:
            Runtime: python3.x
            Role: arn:aws:iam:...:role/lambda-role
            Handler: index.handler
            Code:
                S3Bucket: my-bucket
                S3Key: function.zip
                S3ObjectVersion: String
```

## Through S3 multiple accounts

![](2022-05-12-09-33-18.png)