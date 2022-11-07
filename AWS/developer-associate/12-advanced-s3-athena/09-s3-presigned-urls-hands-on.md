# S3 Pre-signed URLs hands on

We can pre-sign objects with following CLI commands:

```console
$ aws s3 presign s3://mybucket/myobject --region my-region
```

We can add a custom expiration time

```console
$ aws s3 presign s3://mybucket/myobject --expires-in 300 --region my-region
```

If you are getting issues - set the proper signature version in order not to get issues when generating URLs for encrypted files

```console
$ aws configure set default.s3.signature_version s3v4
```