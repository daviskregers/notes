# S3 Encryption for objects

- There are 4 methods of encrypting objects in S3
    - SSE-S3: encrypts S3 objects using keys handled & managed by AWS
        - Object is encrypted server side
        - AES-256 encryption type
        - Must set header `"x-amz-server-side-encryption": "AES256"`
    - SSE-KMS: leverage AWS Key Management Service to mange encryption keys
        - KMS Advantages: user control + audit trail
        - Object is encrypted server side
        - Must set header `"x-amz-server-side-encryption": "aws:kms"`
    - SSE-C: when you want to manage your own encryption keys
        - Amazon S3 does not store the encryption key you provide
        - HTTPS must be used
        - Encryption key must be provided in HTTP headers, for every HTTP request made
    - Client Side Encryption
        - Client library such as Amazon S3 Encryption Client
        - Clients must encrypt data themselves before sending to S3
        - Clients must decrypt data themselves when retrieving from S3
        - Customer fully manages the keys and encryption cycle

## Encryption in transit (SSL)

- AWS S3 exposes
    - HTTP endpoint: non encrypted
    - HTTPS endpoint: encryption in flight

- You're free to use the endpoint you want, but https is recommended
- HTTPS is mandatory for SSE-C
- Encryption in flight is also called SSL/TLS

![](2019-12-30-11-59-39.png)

![](2019-12-30-12-00-13.png)