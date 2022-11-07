# S3 Buckets and Objects hands on

We can open up the S3 in AWS Console.
Here we can view and create our first bucket.

![](2022-02-10-06-31-05.png)

Next, we have to give the bucket name. The name has to be unique across all the accounts in AWS. Then, you have to choose a region (the console is global, but the buckets are not).

![](2022-02-10-06-35-14.png)

Then there's an option to define the ownership:

![](2022-02-10-06-33-29.png)

We can choose the block public access settings

![](2022-02-10-06-36-39.png)

Also, we can set the versioning, tags, encryption and object locks.

![](2022-02-10-06-37-45.png)

Upon finishing the process, we'll see the bucket.

![](2022-02-10-06-38-21.png)

When we open up it up, we can upload our first object. We click on upload and then add files.

![](2022-02-10-06-41-02.png)

Upon uploading we can also see the Destination and other settings as well.

![](2022-02-10-06-42-57.png)
![](2022-02-10-06-43-14.png)
![](2022-02-10-06-43-25.png)

When we click on upload, it should start uploading and display it's status as succeeded when finished.

![](2022-02-10-06-44-09.png)

It will show up when viewing the bucket as well.

![](2022-02-10-06-44-25.png)

When clicking on it - we can see the details of it.

![](2022-02-10-06-45-00.png)

To open up the object we have 2 option on how to do that.
- Click on open when viewing it

![](2022-02-10-06-46-07.png)

- Use the public object URL

![](2022-02-10-06-46-28.png)

This by default give an error because the bucket is not public. The URLs for both look very similar, but the first one is a pre-signed URL.

---

We can also create folders:

![](2022-02-10-06-48-43.png)

And delete the objects:

![](2022-02-10-06-49-05.png)