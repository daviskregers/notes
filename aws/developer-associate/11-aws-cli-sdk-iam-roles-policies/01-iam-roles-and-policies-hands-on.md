# IAM Roles and Policies Hands On

In IAM we can have roles that have policies attached to them.

![](img/2022-02-10-07-57-29.png)

These can be:
- AWS Created policies
- Inline policies (use discouraged for better management)
- Custom created policies

Each policy is a JSON Document that specifies what user is allowed and what not.

![](img/2022-02-10-07-59-25.png)

---

We can create our own policies by going to Policies and Clicking on Create Policy. Here we can use a visual editor or a JSON file.

![](img/2022-02-10-07-59-55.png)

We can create a policy to allow getting objects from a specific bucket.

![](img/2022-02-10-08-02-44.png)

Now we can give it a name

![](img/2022-02-10-08-03-43.png)

Now we can view the policy:

![](img/2022-02-10-08-04-21.png)

Now we can also attach the policy to roles:

![](img/2022-02-10-08-05-20.png)