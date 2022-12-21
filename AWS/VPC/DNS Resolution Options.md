---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/aws/route-53, development/networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# DNS Resolution Options

## DNS Resolution in VPC

- enableDnsSupport (= [[DNS Resolution Setting]])
    - Default True
    - Helps decide if DNS resolution is supported for the [[VPC]]
    - if True, queries the [[AWS DNS server]] at 169.254.169.253
- enableDnsHostname (= [[DNS hostname setting]])
    - False by default for newly created [[VPC]], true by default for [[default VPC]]
    - Won't do anything unless enable DnsSupport=True
    - If True, assign [[public hostname]] to [[AWS EC2]] instance if it has a [[public IP]]
- If you use custom [[DNS domain name]]s in a [[private zone]] in [[AWS Route 53]], you must set both these attributes to true

![](2020-01-01-17-08-45.png)

![](2020-01-01-17-08-56.png)

![](2020-01-01-17-09-17.png)

![](2020-01-01-17-09-28.png)

If we enable it, we can refresh our [[AWS EC2]] instance list and see that there will be [[Public DNS hostname]]s associated with instances:

![](2020-01-01-17-11-59.png)

We can go to [[AWS Route 53]] and create a [[private zone]]:

![](2020-01-01-17-12-41.png)

Then we can create [[record set]]s like these:

![](2020-01-01-17-13-43.png)

Now we'll have a `demo.foobar.internal` hostname that will resolve in our [[VPC]].

