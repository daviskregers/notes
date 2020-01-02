# AWS Organizations

- Global service
- Allows to manage multiple AWS accounts
- The main account is the master account - you can't change it
- Other accounts are member accounts
- Member accounts can only be part of one organization
- Consolidated Billing accross all accounts - single payment method
- Pricing benefits from aggregated usage (volume discount for EC2, S3...)
- API is available to automate AWS account creation

## OU & Service Control Policies (SCPs)

- Organize accounts in Organizational Unit (OU)
    - Can be anything: dev / test / prod or FInance / HR / IT
    - Can nest OU within OU
- Apply Service Control Policies (SCPs) to OU
    - Permit / Deny access to AWS services
    - SCP has a similar syntax to IAm
    - It's a filter to IAM
- Help sandbox account creation
- Help to separate dev and prod resources
- Helpful to only allow approved services
