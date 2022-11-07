# IAM Hands on

You can navigate to IAM though your AWS Console:

![iam-console](iam-console.png)

You can see straight away that the IAM is global and doesn't require region selection:

![iam-global](iam-global.png)

---

Currently we are using a root user (which can be seen when clicking on your username).

![root-user](root-user.png)

We are going to go to `Users` and `Add user` since the root user has all the permissions and we only want to use the root
user for what's truly necessary. Instead we would create an user that is an administrator.

![iam-add-user](iam-add-user.png)

In the next form we are choosing the username and checking the `AWS Management Console Access`.

![iam-new-user](iam-new-user.png)

In the next view we are going to create a group.

![iam-create-group](iam-create-group.png)

We are going to name the grop `admin` and give it `AdministratorAccess` policy.

![admin-group](admin-group.png)

![admin-group-attached](admin-group-attached.png)

In the next screen you can add tags that can be used for categorizing resources.

![iam-tags](iam-tags.png)

And the last step is to verify that everything is added correctly and click on `Create user`.

![iam-user-review](iam-user-review.png)

Once it's created, you can download a CSV with the credentials or send an email with instructions.

We can visit the user section and see that the user has been created, it has an AdministratorAccess permission,
which is inheritted from admin group.

![iam-user-created](iam-user-created.png)

---

We can also go to the `IAM -> Dashboard` and customize the sign-in link:

![iam-signin-link](iam-signin-link.png)
![iam-signin-link-edit](iam-signin-link-edit.png)

--- 

If we visit the sign-in link, we can log in with the new account:

![iam-singin-form](iam-singin-form.png)

![iam-account](iam-account.png)
