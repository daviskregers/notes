# Running the function from the CLI

## Invoking the function from our computer using Serverless

We can use the `sls invoke` to call the function from our local machine.

```console
➜  hello-world-python git:(master) ✗ sls invoke -f hello -l
"hello-world"
--------------------------------------------------------------------
START RequestId: 0c5349b9-c63a-4017-8f9f-9a8857ce0f91 Version: $LATEST
Hi!
END RequestId: 0c5349b9-c63a-4017-8f9f-9a8857ce0f91
REPORT RequestId: 0c5349b9-c63a-4017-8f9f-9a8857ce0f91  Duration: 0.36 ms       Billed Duration: 1 ms   Memory Size: 1024 MB    Max Memory Used: 23 MB
```