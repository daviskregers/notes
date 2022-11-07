# DNS Resolution Options & Route 53 Private Zones

## DNS Resolution in VPC

- enableDnsSupport (= DNS Resolution Seting)
    - Default True
    - Helps decide if DNS resolution is supported for the VPC
    - if True, queries the AWS DNS server at 169.254.169.253
- enableDnsHostname (= DNS hostname setting)
    - False by default for newly created VPC, true by default for default VPC
    - Won't do anything unless enable DnsSupport=True
    - If True, assign public hostname to EC2 instance if it has a public IP
- If you use custom DNS domain names in a private zone in Route 53, you must set both these attributes to true

![](2020-01-01-17-08-45.png)

![](2020-01-01-17-08-56.png)

![](2020-01-01-17-09-17.png)

![](2020-01-01-17-09-28.png)

If we enable it, we can refresh our EC2 instance list and see that there will be Public DNS hostnames associated with instances:

![](2020-01-01-17-11-59.png)

We can go to Route53 and create a private zone:

![](2020-01-01-17-12-41.png)

Then we can create record sets like these:

![](2020-01-01-17-13-43.png)

Now we'll have a `demo.foobar.internal` hostname that will resolve in our VPC.

