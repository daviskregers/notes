# DynamoDB - Security & Other Features

- Security
    - VPC Endpoints available to access DynamoDB without using the Internet
    - Access fully controlled by IAM
    - Encryption at rest using AWS KMS and in-transit using SSL/TLS
- Backup and Restore feature available
    - Point-in-time Recovery (PITR) like RDS
    - No performance impact
- Global Tables
    - Multi-region, multi-active, fully replicated, high performance
- DynamoDB Local
    - Develop and test apps locally without acessing the DynamoDB web service (without internet)
- AWS Database Migration Service (AWS DMS) can be used to migrate to DynamoDB (from MongoDB, Oracle, MySQL, S3, ...)

## Users interact with DynamoDB Directly

![](2022-05-17-08-49-37.png)

## Fine-Grained Access Control

- Using Web Identity Federation or Cognito Identity Pools, each user gets AWS credentials
- You can assign an IAM Role to these users with a Condition to limit their API access to DynamoDB
- LeadingKeys - limit row-level access for users on primary key
- Attributes - limit specific attributes the user can see

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:GetItem", "dynamodb:BatchGetItem", "dynamodb:Query", "dynamodb:PutItem", "dynamodb:UpdateItem", "dynamodb:DeleteItem",
                "dynamodb:BatchWriteitem"
            ],
            "Resource": "arn:aws:dynamodb:us-west-2:123...:table/MyTable",
            "Condition": {
                "ForAllValues:StringEquals": {
                    "dynamodb:LeadingKeys": ["${cognito-identity.amazonaws.com:sub"]
                }
            }
        }
    ]
}
```

more at https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/specifying-conditions.html
