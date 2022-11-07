# IAM Best Practices

- Don't use the root account for AWS account setup
- One physical = one AWS user
- Assign users to groups and assign permissions to groups
- Create a strong password policy
- Use and enforce the use of Multi Factor Authentication (MFA)
- Create and use Roles for giving permissions to AWS services
- Use Access Keys for Programmatic Acces (CLI/SDK)
- Audit permissions of your account with the IAM Credentials Report
- **Never share IAM users & access keys**