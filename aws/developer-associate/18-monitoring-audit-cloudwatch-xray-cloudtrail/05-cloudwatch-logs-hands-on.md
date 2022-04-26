# CloudWatch Logs Hands On

If we open up CloudWatch Logs, we can see multiple Log groups.

![](img/2022-04-26-16-26-41.png)

If we open one up, we can see all the log streams related to it.

![](img/2022-04-26-16-27-28.png)

And, when opening up a log stream, we can see all the events.

![](img/2022-04-26-16-27-55.png)

We can use the search bar to filter the log lines, e.g. containing HTTP.

![](img/2022-04-26-16-28-32.png)

---

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

## Creating Subscription Filters

![](img/2022-04-26-16-36-03.png)

## Edit retention settings

![](img/2022-04-26-16-36-52.png)

![](img/2022-04-26-16-37-01.png)

## Export to Amazon S3

![](img/2022-04-26-16-37-25.png)

![](img/2022-04-26-16-37-42.png)

![](img/2022-04-26-16-38-29.png)

## Create Log Group

![](img/2022-04-26-16-39-40.png)

![](img/2022-04-26-16-39-57.png)

You can setup the retention settings and the KMS ARN if you want the logs to be encrypted.

## Log insights

You can also use Logs Insights to query the logs with a query languange and visusualize it.

![](img/2022-04-26-16-41-30.png)

![](img/2022-04-26-16-41-48.png)

You can also export the results.

![](img/2022-04-26-16-42-17.png)

And save the queries on the right side or look up some queries.

![](img/2022-04-26-16-42-37.png)

