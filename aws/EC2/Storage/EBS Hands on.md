---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/ec2/storage/ebs, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# EBS Hands on

We are going to AWS console, EC2 panel and launch a new instance, every step will be the same as in the previous sections, but there is a step for storage, that we're interested in.

![](2019-12-30-06-45-26.png)

Here we can change the size of the root partition as well as the volume type and IOPS.

![](2019-12-30-06-46-42.png)

We are also going to add an extra volume on /dev/sdb. When chosing this option, we can also create the drive from a snapshot, but since we don't have one, we'll leave it empty. 

We can also choose to use encryption, but it will not interest us this time.

![](2019-12-30-06-48-02.png)

After instance creation, when we go to the Volume section, we can see that there are 2 volumes created:

![](2019-12-30-06-53-05.png)

If we ssh into the ec2 instance, we can see that the volume has been attached.

```
➜  ~ ssssh ec2-user@52.16.251.221 -i ~/Downloads/EC2Tutorial.pem
The authenticity of host '52.16.251.221 (52.16.251.221)' can't be established.
ECDSA key fingerprint is SHA256:C/H5J7MVMWQCW0A6ono1JmijSvo07HqEbrjRCG8FcFw.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '52.16.251.221' (ECDSA) to the list of known hosts.

       __|  __|_  )
       _|  (     /   Amazon Linux 2 AMI
      ___|\___|___|

https://aws.amazon.com/amazon-linux-2/
8 package(s) needed for security, out of 17 available
Run "sudo yum update" to apply all updates.
[ec2-user@ip-172-31-20-13 ~]$ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0   8G  0 disk 
└─xvda1 202:1    0   8G  0 part /
xvdb    202:16   0   8G  0 disk 
```

If we use following command and get `data`, that means that we have to format the drive and mount it:

```
[ec2-user@ip-172-31-20-13 ~]$ sudo file -s /dev/xvd
/dev/xvd: cannot open (No such file or directory)
[ec2-user@ip-172-31-20-13 ~]$ sudo file -s /dev/xvdb
/dev/xvdb: data
[ec2-user@ip-172-31-20-13 ~]$ sudo mkfs -t ext4 /dev/xvdb
mke2fs 1.42.9 (28-Dec-2013)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
524288 inodes, 2097152 blocks
104857 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2147483648
64 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Allocating group tables: done                            
Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done 

[ec2-user@ip-172-31-20-13 ~]$ sudo mkdir /data
[ec2-user@ip-172-31-20-13 ~]$ sudo mount /dev/xvdb /data
[ec2-user@ip-172-31-20-13 ~]$ sudo touch /data/hello-drive
[ec2-user@ip-172-31-20-13 ~]$ sudo ls /data
hello-drive  lost+found
```

Then, we can backup and modify the `/etc/fstab` file so the volume automatically mounts on reboot.

```
[ec2-user@ip-172-31-20-13 ~]$ sudo cp /etc/fstab /etc/fstab.orig
[ec2-user@ip-172-31-20-13 ~]$ sudo vim /etc/fstab
```

```
#
UUID=e8f49d85-e739-436f-82ed-d474016253fe     /           xfs    defaults,noatime  1   1
# Add new EBS Volume
/dev/xvdb /data ext4 defaults,nofail 0 2
```

To test that it works:

```
[ec2-user@ip-172-31-20-13 ~]$ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0   8G  0 disk 
└─xvda1 202:1    0   8G  0 part /
xvdb    202:16   0   8G  0 disk /data
[ec2-user@ip-172-31-20-13 ~]$ sudo umount /data
[ec2-user@ip-172-31-20-13 ~]$ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0   8G  0 disk 
└─xvda1 202:1    0   8G  0 part /
xvdb    202:16   0   8G  0 disk 
[ec2-user@ip-172-31-20-13 ~]$ sudo mount -a
[ec2-user@ip-172-31-20-13 ~]$ lsblk
NAME    MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
xvda    202:0    0   8G  0 disk 
└─xvda1 202:1    0   8G  0 part /
xvdb    202:16   0   8G  0 disk /data

```