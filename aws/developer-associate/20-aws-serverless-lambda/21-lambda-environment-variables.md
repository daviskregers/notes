# Lambda Environment Variables

- Environment variable = key / value pair in string form
- Adjust the function behavior without updating the code
- The environment variables are available to your code
- Lambda Service adds it own system environment variables as well

- Helpful to store secrets (encrypted by KMS)
- Secrets can be encrypted by the Lambda service key, or your own CMK