---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-11-24
sr-interval: 2
sr-ease: 210
---

## Volume Encryption

- When you create an encrypted [[EBS Volume]], you get the following:
    - Data at rest is encrypted inside the volume
    - All the data in flight moving between the instance and volume is encrypted
    - All snapshots are encrypted
- Encryption and decryption are handled transparently (you have nothing to do)
- Encryption has a minimal impact on latency
- EBS Encryption leverages keys from [[AWS KMS (Key Management Service)]] ([[AES-256]])
- Copying an unencrypted snapshot allows encryption
- Snapshots of encrypted volumes are encrypted

### Encrypt an unencrypted EBS volume

- Create an [[EBS Snapshot]] of the volume
- Encrypt the EBS snapshot (using copy)
- Create a new EBS volume from the snapshot (the volume will also be encrypted)
Now you can attach the encrypted volume to the original instance.

![](2019-12-30-07-29-28.png)

![](2019-12-30-07-30-20.png)

![](2019-12-30-07-31-10.png)

![](2019-12-30-07-32-00.png)

![](2019-12-30-07-32-22.png)