# AWS Lambda Pricing

You can find overall pricing information here: https://aws.amazon.com/lambda/pricing

For us-east1 region as of June 2017 it is:

- Pay per calls
    - First 1,000,000 requests are free
    - 0.20 per 1 million requests after
- Pay per duration (in increment of 100ms)
    - 400,000 GB-seconds of compute time per month are free
    - 400,000 seconds if function is 1 GB RAM
    - 3,200,000 seconds if function is 128MB RAM
    - After that $1.00 for 600,000 GB-seconds

It is usually very cheap to run AWS Lambda so it's very popular.