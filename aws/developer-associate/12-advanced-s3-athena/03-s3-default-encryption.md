# S3 Default Encryption vs Bucket Policies

- One way to "enforce encryption" is to use a bucket policy and refuse any API call to PUT and S3 object without encryption headers.
- Another way is to use "default encryption" option in S3
- Note: bucket policies are evaluated before default enctyption.

We can manage this in the S3 bucket properties:

![](2022-02-17-06-40-54.png)