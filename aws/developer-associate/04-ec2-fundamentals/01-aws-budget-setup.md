# AWS Budget Setup

In order not to spend too much, we are first going to set up a budget.

When you are logged into your AWS account, click on your username and go to `My Billing Dashboard`.

![](img/2021-08-17-11-38-30.png)

When you are visiting the billing page, an error might come up saying that you need permissions.

![](img/2021-08-17-11-40-46.png)

This can be fixed by accessing your root account. Then click on our username and go to `My Account`.

![](img/2021-08-17-11-44-07.png)

We are going to scroll down and access the page called `IAM User And Role Access To Billing Information`. Then we are going to activate it.

![](img/2021-08-17-11-45-06.png)

After that, we can access the billing information with users that have the IAM permissions set, e.g., administrators.

![](img/2021-08-17-11-47-27.png)

Here we cann view all the bills that we have previously had, explore the costs etc. 

We are going to open up the `Budgets` section and add a new budget, with a type `Cost Budget`. We are going to set up a monthly recurring budget with a fixed amount that we are willing to spend each month.

![](img/2021-08-17-11-52-16.png)

In the next step we can configure thresholds. This is for configuring notifications that will alert you that you have reached a certain threshold in your spending.

![](img/2021-08-17-11-54-52.png)