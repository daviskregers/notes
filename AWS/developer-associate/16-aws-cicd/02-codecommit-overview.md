# CodeCommit Overview

- Version control is the ability to understand the various changes that happened to the code over time (and possibly roll back)
- All these are enabled by using a version control system such as Git
- A Git repository can be synchronized on your computer but it usually is uploaded on a central online repository
- Benefits are:
    - Collaborate with other developers
    - Make sure the code is backed-up somewhere
    - Make sure it's fully viewable and auditable

## CodeCommit

- Git repositories can be expensive
- The industry includes GitHub, GitLab, BitBucket, ...
- And AWs CodeCommit:
    - Private Git repositories
    - No size limit on repositories (scale seamlessly)
    - Fully managed, highly available
    - Code only in AWS Cloud account => increased security and compliance
    - Security (encrypted, access control, ...)
    - Integrated with Jenkins, AWS CodeBuild and other CI tools

## Security

- Interactions are done using Git (standard)
- Authentication
    - SSH keys - aws users can configure SSH keys in their IAM Console
    - HTTPS - with AWS CLI Credential helper or Git Credentials for IAM user
- Authorization
    - IAM policies to manage users/roles permissions to repositories
- Encryption
    - Repositories are automatically encrypted at rest using AWS KMS
    - Encrypted in transit (can only use HTTPS or SSH - both secure)
- Cross-account Access
    - DO NOT share your SSH keys or your AWS credentials
    - Use an IAM Role in your AWS account and use AWS STS (AssumeRole API)

## CodeCommit vs GitHub

|                                     | CodeCommit              | GitHub                                                          |
|-------------------------------------|-------------------------|-----------------------------------------------------------------|
| Support Code Review (Pull Requests) | y                       | y                                                               |
| Integration with AWS CodeBuild      | y                       | y                                                               |
| Authentication (SSH & HTTPS)        | y                       | y                                                               |
| Security                            | IAM Users & Roles       | Github users                                                    |
| Hosting                             | Managed & hosted by AWS | Hosted by Github Github enterprise: self hosted on your servers |
| UI                                  | minimal                 | fully featured                                                  |