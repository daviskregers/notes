---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/lambda, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# KMS And Lambda practice

## [[AWS KMS (Key Management Service)]]

In [[AWS KMS (Key Management Service)]] we have a [[AWS Managed keys]] section available that stores keys for aws managed services that we have had enabled encryption.


![](2020-01-01-14-17-26.png)

You can also go to [[Customer managed keys]] and create your own keys.

![](2020-01-01-14-20-25.png)

When created a key, we can also open it up and enable key rotation:

![](2020-01-01-14-21-23.png)

## [[AWS Lambda]]

We are going to create a new lambda function.

![](2020-01-01-14-22-46.png)

Now, if we wanted to use database password, this is bad:

```python
import json
dbpassword = "supersecret"

def lambda_handler(event, context):
    return dbpassword
```

We can leverage [[environment variables]] though, but it is still not perfect, because if someone accesses the [[AWS Lambda]] UI, the password is still visible.

We can leverage the encryption option with the previously created `Customer managed key` though.

![](2020-01-01-14-26-30.png)

Now if we change the code to run this:

```python
import boto3
import os

from base64 import b64decode

ENCRYPTED = os.environ['DB_PASSWORD']
# Decrypt code should run once and variables stored outside of the function
# handler so that these are decrypted once per container
DECRYPTED = boto3.client('kms').decrypt(CiphertextBlob=b64decode(ENCRYPTED))['Plaintext'].decode('utf-8')

def lambda_handler(event, context):
    print(ENCRYPTED)
    print(DECRYPTED)
    return DECRYPTED
```

When testing, we will get an error:

```
An error occurred (AccessDeniedException) when calling the Decrypt operation: The ciphertext refers to a customer master key that does not exist, does not exist in this region, or you are not allowed to access.
```

This is because our [[AWS Lambda]] function does not have the permission to decrypt it.

We are going to open up a new tab with the `View the lamda-demo-kms-role-fo9pvnp8 role`.

![](2020-01-01-14-31-25.png)

Then create and attach a [[IAM Policy]].

![](2020-01-01-14-33-34.png)

![](2020-01-01-14-35-24.png)

![](2020-01-01-14-35-42.png)

Test it once more:

![](2020-01-01-14-36-02.png)

If we view the logs, we can see the both prints of the [[encrypted]] and [[decrypted]] versions:

![](2020-01-01-14-37-12.png)