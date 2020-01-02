# RDS Security for SysOps

- Encryption at rest
    - Is done only when you first create the DB Instance
    - or create snapshot from the database, copy snapshot as encrypted, create DB from snapshot
- Your responsibility
    - Check the ports / IP / Security group inbound rules for DB's Security Group
    - In-database user creation and permissions
    - Creating a database with or without public access
    - Ensure parameter groups or DB is configured to only allow SSL connections
- AWS responsibility
    - No SSH access
    - No manual DB patching
    - No OS patching
    - No way to audit the underlying instance