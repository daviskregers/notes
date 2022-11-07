---
Created: 2022-11-08 08:37:32
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/fundamentals]
---

# AWS Budget Setup

As mentioned in previous section, most of the course will utilize free tier, but in case our account does go over it, we will setup budget so we receive a notification when exceeding the free tier and not spending too much.

In order to do this, we go click on `My Account` and going to `My Billing Dashboard`, Then on the left side there will be an option called `Budgets`.

Then click on a `Create Budget` -> `Cost Budget`.

![](../../../images/2019-11-22-09-48-07.png)

When configuring alerts, we'll set an alert on $0.01, so we'll know when we have exceeded the free tier.

![](../../../images/2019-11-22-09-48-45.png)