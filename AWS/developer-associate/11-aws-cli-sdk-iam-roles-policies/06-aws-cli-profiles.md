# AWS CLI Profiles

When we configure our CLI it creates a default profile, that is stored in `~/.aws/credentials`, but we can also set other profiles as well.

```console
$ aws configure --profile my-other-aws-account
$ cat ~/.aws/credentials
[default]
aws_access_key_id = ...
aws_secret_access_key = ...
[my-other-aws-account]
aws_access_key_id = ...
aws_secret_access_key = ...
$ cat ~/.aws/config
[default]
region = eu-west3
[profile my-other-aws-account]
region = us-west-2
```

Now you can use this profile for CLI calls:

```console
$ aws s3 ls --profile my-other-aws-account
```
