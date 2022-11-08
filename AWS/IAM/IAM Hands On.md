---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/iam, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# IAM Hands on

We can go to the AWS Console and navigate to the IAM service.

When we're starting, there is virtually nothing in our accounts:

![](../../../images/2019-11-22-10-10-01.png)

Below there is a security status listed that tells what we can do to improve security.

![](../../../images/2019-11-22-10-10-48.png)

- So, we are going to:
    - Delete the ROOT access keys
    - Setup MFA for the root user
    - Create a new user

    ![](../../../images/2019-11-22-10-14-34.png)

    ![](../../../images/2019-11-22-10-15-11.png)

    ![](../../../images/2019-11-22-10-15-59.png)

    ![](../../../images/2019-11-22-10-17-16.png)

    - Manage groups

    ![](../../../images/2019-11-22-10-18-30.png)

    ![](../../../images/2019-11-22-10-18-57.png)

    ![](../../../images/2019-11-22-10-19-38.png)

    ![](../../../images/2019-11-22-10-20-27.png)

    ![](../../../images/2019-11-22-10-20-45.png)

    Now we can go to the user `davis` and detach the permissions, since it's not directly manageable.

    ![](../../../images/2019-11-22-10-22-10.png)

    ![](../../../images/2019-11-22-10-22-29.png)

    - Setup IAM password policy

    ![](../../../images/2019-11-22-10-23-09.png)

    ![](../../../images/2019-11-22-10-24-58.png)

Now, the security should be set up.

![](../../../images/2019-11-22-10-25-23.png)

The last step is to create an account alias for editing the sign-in link into their accounts.

![](../../../images/2019-11-22-10-27-07.png)

Now we can log out of the root user and got to the admin account we created.

![](../../../images/2019-11-22-10-31-07.png)

And it will then ask us for changing the password because of the password policy we set up.

![](../../../images/2019-11-22-10-32-20.png)

![](../../../images/2019-11-22-10-34-36.png)