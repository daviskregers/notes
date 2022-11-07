# S3 Replication (CRR & SRR)

- Must enable versioning in source and destination
- Cross Region Replication (CRR)
- Same Region Replication (SRR)
- Buckets can be in different accounts
- Copying is asynchronous
- Must give proper IAM permissions to S3
- CRR - Use cases: compliance, lower latency access, replication across accounts.
- SRR - Use cases: log aggregation, live replication between production and test accounts

## Notes

- After activating, only new objects are replicated (not rectroactive)
- For DELETE operations:
    - Can replicate delete markers from source to target (optional setting)
    - Deletions with a version ID are not replicated (to avoid malicious deletes)
- There is no "chaining" of replication
    - If bucket 1 has replication into bucket 2, which has replication into bucket 3
    - Then objects created in bucket 1 are not replicated into bucket 3