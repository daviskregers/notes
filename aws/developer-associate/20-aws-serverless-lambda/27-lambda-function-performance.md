# Lambda Function Performance

## Lambda Function Configuration

- RAM
    - From 128 MB to 10GB in 1MB increments
    - The more RAM you add, the more vCPU credits you get
    - At 1,792 MB, a function has the equivalent of one full vCPU
    - After 1,792 MB, you get more than one CPU, and need to use multi-threading in your code to benefit from it.
- If your application is CPU-bound (computation heavy), increase RAM
- Timeout: default 3 seconds, maximum 900 seconds (15 minutes)

## Lambda Execution Context

- The execution context is a temporary runtime environment that initializes any external dependencies of your lambda code
- Great for database connections, HTTP clients, SDK clients...
- The execution context is maintained for some time in anticipation of another Lambda function invocation
- The next function invocation can "re-use" the context to execution time and save time in initializing connections objects.
- The execution context includes the /tmp directory.

## Initialize outside the handler

### BAD

```python
import os

def get_user_handler(event, context):
    DB_URL = os.get_env("DB_URL")
    db_client = db.connect(DB_URL)
    user = db_client.get(user_id = event["user_id"])

    return user
```

The DB connection is established at every function invocation.

### GOOD

```python
import os

DB_URL = os.get_env("DB_URL")
db_client = db.connect(DB_URL)

def get_user_handler(event, context):
    user = db_client.get(user_id = event["user_id"])

    return user
```

The DB connection is established once and re-used across invocations.

## Lambda Functions /tmp space

- If your Lambda function needs to download a big file to work
- If your Lambda function needs disk space to perform operations
- You can use the /tmp directory
- Max size is 512MB
- The directory content remains when the execution context is frozen, providing transient cache that can be used for multiple invocations (helpful to checkpoint your work)
- For permanent persistence of object (non temporary), use S3