# Lambda Concurrency

- Concurrency limit: up to 1000 concurrent executions
- Can set a reserved concurrency at the function level
- Each invocation over the concurrency limit will trigger a throttle
- Throttle behavior
    - If syncronous invocation - return ThrottleError - 429
    - If asynchronous invocation - retry automaticall and then go to DLQ

## Concurrency and Asynchronous Invocations

- If the function doesn't have enough concurrency available to process all events, additional requests are throttled.
- For throttling errors (429) and system errors (500-series), Lambda returns the event to the queue and attempts to run the function again for up to 6 hours.
- The retry interval increases exponentially from 1 second after the first attempt to a maximum of 5 minutes.

![](2022-05-12-09-12-33.png)

## Cold Starts & Provisioned Concurrency

- Cold Start
    - New instance -> code is loaded and code outside the handler run (init)
    - If the init is large (code, dependencies, SDK) this process can take some time
    - First request is served by new instances has higher latency than the rest
- Provisioned Concurrency
    - Concurrency is allocated before the function is invoked (in advance)
    - So the cold start never happens and all invocations have low latency
    - Application Auto Scaling can manage concurrency (schedule or target utilization)
- Note:
    - cold starts in VPC have been dramatically reduced in Oct & Nov 2019
    - https://aws.amazon.com/blogs/compute/announcing-improved-vpc-networking-for-aws-lambda-functions/

## Reserved and Provisioned Concurrency

![](2022-05-12-09-15-58.png)

https://docs.aws.amazon.com/lambda/latest/dg/configuration-concurrency.html