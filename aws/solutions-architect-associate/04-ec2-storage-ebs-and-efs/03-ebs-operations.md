# EBS Operations

## EBS Snapshots

- Incremental - only backups changed blocks
- EBS Backups use IO and you shouldn't run them while your application is handling a lot of traffic
- Snapshots will be stored in S3 (but you won't directly see them)
- Not necessary to detach volume to do snapshot, but recommended
- Max 100,000 snapshots
- Can copy snapshots accross AZ or Region
- Can make Image (AMI) from snapshot
- **EBS volumes restored by snapshots need to be pre-warmed (using fio or dd command to read the entire volume)**
- **Snapshots can be automated using Amazon Data Lifecycle Manager**

The snapshots can be created by right-clicking on the volume.

![](2019-12-30-07-15-22.png)

![](2019-12-30-07-16-44.png)

![](2019-12-30-07-17-09.png)

When the snapshot is created we can do several operations with it:
- Create a new volume from the snapshot
- Create Image (AMI) from the snapshot

![](2019-12-30-07-18-12.png)

We can also go to the `Lifecycle Manger` section and add a new snapshot policy, like we are going to make snapshots for all the volumes that have a tag `EBS Demo` every 12 hours and keep the last 7 copies.

![](2019-12-30-07-21-32.png)

## EBS Migration

- EBS Volumes are only locked to a specific AZ
- To migrate it to a different AZ (or region):
    - Snapshot the volume
    - (optional) Copy the volume to a different region
    - Create a volume from the snapshot in the AZ of your choice

![](2019-12-30-07-24-15.png)
![](2019-12-30-07-24-36.png)
![](2019-12-30-07-25-11.png)

## Volume Encryption

- When you create an encrypted EBS volume, you get the following:
    - Data at rest is encrypted inside the volume
    - All the data in flight moving between the instance and volume is encrypted
    - All snapshots are encrypted
- Encryption and decryption are handled transparently (you have nothing to do)
- Encryption has a minimal impact on latency
- EBS Encryption leverages keys from KMS (AES-256)
- Copying an unencrypted snapshot allows encryption
- Snapshots of encrypted volumes are encrypted

### Encrypt an unencrypted EBS volume

- Create an EBS snapshot of the volume
- Encrypt the EBS snapshot (using copy)
- Create a new EBS volume from the snapshot (the volume will also be encrypted)
Now you can attach the encrypted volume to the original instance.

![](2019-12-30-07-29-28.png)

![](2019-12-30-07-30-20.png)

![](2019-12-30-07-31-10.png)

![](2019-12-30-07-32-00.png)

![](2019-12-30-07-32-22.png)