# S3 MFA Delete Hands On

We can create a new S3 bucket, make sure it's versioning is turned on.

---

Then we'll see that under the Versioning there is an option for multi-factor authentication delete, but we cannot activate it through the console.

![](2022-02-17-06-25-07.png)

---

We can go into our root user, make sure that MFA is enabled for it. Make a access key for the root user.

![](2022-02-17-06-32-01.png)
![](2022-02-17-06-32-25.png)
![](2022-02-17-06-32-38.png)

---

We can then enable the MFA delete:

```console
$ aws s3api put-bucket-versioning --bucket BUCKETNAME --versioning-configuration Status=Enabled,MFADelete=Enabled --mfa "MFA:ARN CODE" --profile root-profile
```

![](2022-02-17-06-36-41.png)

Disabling MFA delete:

```console
$ aws s3api put-bucket-versioning --bucket BUCKETNAME --versioning-configuration Status=Enabled,MFADelete=Disabled --mfa "MFA:ARN CODE" --profile root-profile
```

![](2022-02-17-06-37-58.png)