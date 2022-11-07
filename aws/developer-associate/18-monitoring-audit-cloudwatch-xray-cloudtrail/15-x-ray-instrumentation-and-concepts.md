# X-Ray Instrumentation and Concepts

- Instrumentation means the measure of product's performance, diagnose errors, and to write trace information.

- To instrument your application code, you use the X-Ray SDK
- Many SDK require only configuration changes
- YHou can modify your application code to customize and annotate the data that the SDK sends to X-Ray, using interceptors, filters, handlers, middleware.

## Concepts

- Segments: each application / service will send them
- Subsegments: if you need more details in your segment
- Trace: segments collected together to form an end-to-end trace
- Sampling: decrease the amount of requests sent to X-Ray, reduce cost
- Annotations: Key Value pairs used to index traces and use with filters
- Metadata: Key Value pairs, not indexed, not used for searching

- The X-Ray deaemon / agent has a config to send traces cross account:
    - make sure the IAM permissions are correct - the agent will assume the role.
    - This allows to have a central account for all your application tracing.

## Sampling Rules

- With sampling rules, you control the amount of data that you record
- You can modify sampling rules without changing your code

- By default, the X-Ray SDK records the first request each second, and five percent of any additional requests
- One request per second is the reservoir, which ensures that at least one trace is reacorded each second as long the service is serving requests.
- Five percent is the rate which additional requests beyond the reservoir size are sampled.

---

You can create your own rules with the reservoir and rate.

![](2022-04-26-17-41-54.png)