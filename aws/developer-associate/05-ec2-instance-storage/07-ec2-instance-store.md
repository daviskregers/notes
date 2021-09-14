# EC2 Instance Store

- EBS volumes are network drives with good but "limited" performance
- If you need a high performance hardware disk, use EC2 instance store

---

- Better I/O performance
- EC2 Instance Store lose their storage if they're stopped (ephemeral)
- Good for buffer / cache / scratch data / temporary content
- Risk of data loss if hardware fails