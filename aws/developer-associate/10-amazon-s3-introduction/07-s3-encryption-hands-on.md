# S3 Encryption Hands On

In the bucket properties we can see a setting for encryption:

![](img/2022-02-10-06-59-03.png)

We can enable it here, but first we can upload a file and do it there:

![](img/2022-02-10-07-00-25.png)

For the KMS we have multiple options:

![](img/2022-02-10-07-01-34.png)

Once uploaded, we open up the files and see that they are encrypted:

![](img/2022-02-10-07-02-51.png)
![](img/2022-02-10-07-03-14.png)

So, we can upload files and define the enctyption settings for each of them, but we can go to the Properties and specify the default encryption mechanism for the whole bucket.

![](img/2022-02-10-07-04-48.png)

Now when we simply upload a new file to the S3:

![](img/2022-02-10-07-05-47.png)

![](img/2022-02-10-07-06-05.png)

---

Note that the other types of encryption doesn't show up because:
- SSE-C needs to be done via the CLI with a provided key
- The client side - the client needs to encrypt the file himself before uploading.

