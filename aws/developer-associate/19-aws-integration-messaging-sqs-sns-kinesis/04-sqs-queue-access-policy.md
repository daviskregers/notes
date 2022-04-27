# SQS Queue Access Policy

## Cross Account

![](img/2022-04-27-06-41-38.png)

```json
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Principal": {"AWS": [111122223333]},
        "Action": ["sqs:ReceiveMessage"],
        "Resource": "arn:aws:sqs:us-east-1:4444555666:queue1"
    }]
}
```

## Publish S3 Event Notifications to SQS Queue

![](img/2022-04-27-06-41-45.png)

```json
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Principal": {"AWS": "*"},
        "Action": ["sqs:SendMessage"],
        "Resource": "arn:aws:sqs:us-east-1:4444555666:queue1",
        "Condition": {
            "ArnLike": {"aws:SourceArn": "arn:aws:s3:*:*:bucket1"},
            "StringEquals": {"aws:SourceAccount":"<bucket1_owner_account_id"}
        }
    }]
}
```

When creating an S3 bucket:

![](img/2022-04-27-06-45-01.png)

![](img/2022-04-27-06-45-35.png)

In SQS:

![](img/2022-04-27-06-46-41.png)

![](img/2022-04-27-06-47-21.png)