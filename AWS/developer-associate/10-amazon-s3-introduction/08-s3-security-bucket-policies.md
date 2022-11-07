# S3 Security & Bucket Policies

## S3 Security

- User Based
    - IAM Roles - which API calls should be allowed for a specific user from IAM console
- Resource Based
    - Bucket Policies - bucket wide rules from the S3 console - allows cross account
    - Object Access Control List (ACL) - finer grain
    - Bucket Access Control List (ACL) - less common
- Note: an IAM principal can access and S3 object if
    - the user IAM permission allow it OR the resource policy ALLOWS it
    - AND there's no explicit DENY

## S3 Bucket Policies

- Json based policies
    - Resources: buckets and objects
    - Actions: Set of API to Allow or Deny
    - Effect: Allow / Deny
    - Principal: The account or user to apply the policy to


```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::examplebucket/*"
            ]
        }
    ]
}
```

- Use S3 bucket for policy to:
    - Grant public access to the bucket
    - Force objects to be encrypted at upload
    - Grant access to another account (cross account)

## Bucket settings for Block Public Access

- Block public access to buckets and objects granted through
    - new access control lists (ACLs)
    - any access control lists (ACLs)
    - new public bucket or access point policies
- Block public and cross-account access to buckets and objects through any public bucket or access point policies

---

- These settings were created to prevent company data leaks
- If you know your bucket should never be public, leave these on
- Can be set at the account level

## S3 Security - Other

- Networking:
    - Supports VPC Endpoints (for instances in VPC without internet)
- Logging and Audit:
    - S3 Access Logs can be stored in other S3 buckets
    - API calls can be logged in AWS CloudTrail
- User Security:
    - MFA (multi-factor auth) delete can be required in versioned buckets to delete objects
    - Pre-signed urls: URLs that are valid only for a limited time