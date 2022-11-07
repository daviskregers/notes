# S3 MFA Delete

- MFA (Multi Factor Authentication) forces user to generate a code on a device (usually a mobile phone or hardware) before doing important operations on S3
- To use MFA-Delete, enable versioning on the S3 bucket
- You will need MFA to:
    - permanently delete an object version
    - suspend versioning on bucket
- You won't need MFA for
    - enabling versioning
    - listing deleted versions

---

- Only the bucket owner (root account) can enable/disable MFA-delete
- MFA-Delete currently can only be enabled using the CLI

