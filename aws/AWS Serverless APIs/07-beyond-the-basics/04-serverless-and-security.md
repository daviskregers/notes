# Serverless and security

While we don't really need to worry about our servers in serverless aproach, we do need to consider following security issues:

- Application related
    - Unauthenticated Access 
        - Protect API endpoints with Cognito / Auth
        - Restricting API usage with API Keys
    - Compromised User Data
        - Cognito uses SSL and ecrypts data
        - Retrieve User data carefully
- Infrastructure related
    - DDoS attacks
        -   Throttling and DDoS protection built-in
    - NoSQL Injection
        - Access through SDK, protection built-in
    - Stolen AWS credentials