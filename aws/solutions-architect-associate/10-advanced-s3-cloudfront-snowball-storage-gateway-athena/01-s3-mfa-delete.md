# S3 MFA Delete

- MFA (Multi factor authentication) forces user to generate a code on a device (usually mobile phone or hardware) before doing important operations on S3
- To use MFA-Delete, enable Versioning on the S3 bucket
- You will need MFA to
    - Permanently delete an object version
    - Suspend version on the bucket
- YOu won't need MFA for
    - Enabling versioning
    - Listing deleted versions

- Only the bucket owner (root acount) can enable/disable MFA-delete
- MFA-Delete currently can only be enabled using the CLI

```
aws s3api put-bucket-versioning --bucket mfa-demo --versioning-configuration Status=Enabled,MFADelete=Enabled --mfa "arn-of-mfa-device mfa-code" --profile root-datacumulus
```

The code can be gotten from `IAM` when multifactor auth is set up.