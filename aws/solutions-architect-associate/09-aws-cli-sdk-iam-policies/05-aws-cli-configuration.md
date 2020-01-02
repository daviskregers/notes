# AWS CLI Configuration

In order to configure AWS CLI we need to get access credentials from `AWS IAM`. It will be located under `Users -> {user} -> Security Credentials -> Access Keys`.

Then we are going to run

```
➜  ~ aws --version
aws-cli/1.16.303 Python/3.8.0 Linux/5.4.2-arch1-1 botocore/1.13.39
➜  ~ aws configure
AWS Access Key ID [None]: XXX
AWS Secret Access Key [None]: XXXX
Default region name [None]: eu-west-1
Default output format [None]: 
➜  ~ aws configure
AWS Access Key ID [****************XXXX]: 
AWS Secret Access Key [****************XXXX]: 
Default region name [eu-west-1]: 
Default output format [None]: 
➜  ~ ls ~/.aws
config  credentials
➜  ~ cat ~/.aws/config 
[default]
region = eu-west-1

```