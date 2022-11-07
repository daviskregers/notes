# AWS Access keys, CLI and SDK

To access AWS, you have 3 options:
- AWS Management Console (protected by password + MFA)
- AWS Command Line Interface (CLI): protected by access keys
- AWS Software Developer Kit (SDK) - for code: protected by access keys

---

- Access Keys are generated through AWS console
- Users manage their own access keys
- **Access keys are secret, just like a password. Don't share them**

## What's a CLI?

- A tool that enables you to interact with AWS services using commands in your command-line shell.
- Direct access to the public APIs of AWS services
- You can develop scripts to manage your resources
- It's open source https://github.com/aws/aws-cli
- Alternative to using AWS Management Console

## What's the AWS SDK?

- AWS Software Development Kit (AWS SDK)
- Language-specific APIs (set of libraries)
- Enables you to access and manage AWS services programmatically
Embedded within your application
- Supports
    - SDKs (Javascript, Python, PHP, .NET, Ruby, Java, Go, Node.js, C++)
    - Mobile SDKs (Android, iOS...)
    - IoT Device SDKs (Embedded C, Arduino, ...)

Example: AWS CLI is built on AWS SDK for Python