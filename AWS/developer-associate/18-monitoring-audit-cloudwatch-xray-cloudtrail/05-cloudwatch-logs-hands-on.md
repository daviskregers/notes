# CloudWatch Logs Hands On

If we open up CloudWatch Logs, we can see multiple Log groups.

![](2022-04-26-16-26-41.png)

If we open one up, we can see all the log streams related to it.

![](2022-04-26-16-27-28.png)

And, when opening up a log stream, we can see all the events.

![](2022-04-26-16-27-55.png)

We can use the search bar to filter the log lines, e.g. containing HTTP.

![](2022-04-26-16-28-32.png)

---

## Creating Metric Filters

![](2022-04-26-16-29-06.png)

### Creating Filter pattern

![](2022-04-26-16-30-13.png)

- Test the filter pattern on a dataset.

![](2022-04-26-16-30-41.png)
![](2022-04-26-16-30-49.png)

### Assign metric

![](2022-04-26-16-32-24.png)

![](2022-04-26-16-33-33.png)

![](2022-04-26-16-33-54.png)

## Review & Create

![](2022-04-26-16-34-25.png)

---

## Creating Subscription Filters

![](2022-04-26-16-36-03.png)

## Edit retention settings

![](2022-04-26-16-36-52.png)

![](2022-04-26-16-37-01.png)

## Export to Amazon S3

![](2022-04-26-16-37-25.png)

![](2022-04-26-16-37-42.png)

![](2022-04-26-16-38-29.png)

## Create Log Group

![](2022-04-26-16-39-40.png)

![](2022-04-26-16-39-57.png)

You can setup the retention settings and the KMS ARN if you want the logs to be encrypted.

## Log insights

You can also use Logs Insights to query the logs with a query languange and visusualize it.

![](2022-04-26-16-41-30.png)

![](2022-04-26-16-41-48.png)

You can also export the results.

![](2022-04-26-16-42-17.png)

And save the queries on the right side or look up some queries.

![](2022-04-26-16-42-37.png)

