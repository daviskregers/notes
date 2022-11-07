# S3 Access logs

- For audit purposes, you may want to log all access to S3 buckets
- Any request made to S3, from any account, authorized or denied, will be logged into another S3 bucket
- That data can be analyzed using data analysis tools
- Or amazon Athena

- The log format is at https://docs.aws.amazon.com/AmazonS3/latest/dev/LogFormat.html

![](2019-12-30-13-12-40.png)