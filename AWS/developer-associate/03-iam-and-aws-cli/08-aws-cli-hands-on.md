# AWS CLI Hands on

You can obtain access key in your IAM account, under `Security Credentials -> Access Keys -> Create Access Keys`.

**Do not generate access credentials for your root account!** Only add them for your IAM accounts.

![](2021-07-26-18-22-23.png)

```
➜  /tmp aws --version
aws-cli/2.2.22 Python/3.8.8 Linux/5.12.15-arch1-1 exe/x86_64.arch prompt/off
➜  /tmp aws configure
AWS Access Key ID [None]: **REDACTED**
AWS Secret Access Key [None]: **REDACTED**
Default region name [None]: eu-west-1
Default output format [None]:
➜  /tmp aws iam list-users
{
    "Users": [
        {
            "Path": "/",
            "UserName": "davis",
            "UserId": "SOME-ID",
            "Arn": "arn:aws:iam::SOME-ID:user/davis",
            "CreateDate": "2021-06-28T10:26:17+00:00",
            "PasswordLastUsed": "2021-07-26T15:15:40+00:00"
        }
    ]
}
```

Note that in order to receive the list of users previously executed, you need to have the permissions to do so in the IAM. If the request is denied - it might return nothing.