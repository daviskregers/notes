# Kinesis Data Firehose Hands On

We are going to create a new data stream.

![](img/2022-04-27-08-25-36.png)

![](img/2022-04-27-08-26-08.png)

![](img/2022-04-27-08-26-20.png)

We have an option to trasform the records with AWS Lambda before they are being delivered by Firehose. Also, we have an option to transform the record format into Apache Parquet or Apache ORC.

![](img/2022-04-27-08-27-40.png)

Next, we are setting the destination

![](img/2022-04-27-08-29-39.png)

Under the additional settings we can configure the buffer size it will wait to fill as well as the interval. For example, it will wait until it fills 1MB buffer or times out at 60 seconds and then writes it into S3.

![](img/2022-04-27-08-31-25.png)

![](img/2022-04-27-08-33-00.png)

![](img/2022-04-27-08-33-24.png)

---

