# CloudWatch Logs Metric Filters

- CloudWatch Logs can use filter expressions
    - For example, find a specific IP inside of a log
    - Or count occurrences of "ERROR" in your logs
    - Metric filters can be used to trigger alarms
- **Filters do not retroactively filter data. Filters only publish the metric data points for events that happen after the filter was created.**

![](img/2022-04-26-09-57-36.png)

## Creating Metric Filters

![](img/2022-04-26-16-29-06.png)

### Creating Filter pattern

![](img/2022-04-26-16-30-13.png)

- Test the filter pattern on a dataset.

![](img/2022-04-26-16-30-41.png)
![](img/2022-04-26-16-30-49.png)

### Assign metric

![](img/2022-04-26-16-32-24.png)

![](img/2022-04-26-16-33-33.png)

![](img/2022-04-26-16-33-54.png)

## Review & Create

![](img/2022-04-26-16-34-25.png)

---

When that's done, after some time, when new logs have came in with the specific criteria - a new Custom Namespace should show up under metrics.

![](img/2022-04-26-16-45-43.png)

We can also use this metric to create a CloudWatch Alarm

![](img/2022-04-26-16-46-25.png)

![](img/2022-04-26-16-46-50.png)

![](img/2022-04-26-16-47-15.png)

![](img/2022-04-26-16-47-43.png)

![](img/2022-04-26-16-48-04.png)

Once it's created we'll see it under alarms.

![](img/2022-04-26-16-48-58.png)

Under metric filters we'll also see that it's linked to an alarm

![](img/2022-04-26-16-49-26.png)