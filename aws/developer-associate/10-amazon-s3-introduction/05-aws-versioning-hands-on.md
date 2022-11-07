# AWS S3 Versioning

We can set up versioning when creating a bucket, but we can also do that for the existing ones.

We can go to the Properties tab and the very first option will be to enable the versioning.

![](2022-02-10-06-50-28.png)

![](2022-02-10-06-50-38.png)

Now in our object list there will be an option to show versions. We can see that when the object is first created, it's version is null.

![](2022-02-10-06-51-56.png)

If we upload a file, we'll see that it will assign version ID to it.

![](2022-02-10-06-53-04.png)

If we upload the same file again, we'll see that the second file now has 2 version IDs.

![](2022-02-10-06-54-00.png)

Now if we toggle off the version information and delete the file:

![](2022-02-10-06-55-16.png)

Now we can see that there is a delete marker added that tells AWS that the file was deleted.

![](2022-02-10-06-56-10.png)

If we delete the delete marker. (this is a permanent delete)

![](2022-02-10-06-57-01.png)

Now we can see that we have rolled back the file to a previous version:

![](2022-02-10-06-57-23.png)

---

If you are to suspend the versioning, all the previously created versions will persist but all the new files will have version number of null.