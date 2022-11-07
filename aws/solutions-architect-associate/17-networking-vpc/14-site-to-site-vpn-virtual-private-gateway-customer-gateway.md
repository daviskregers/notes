# Site to Site VPN, Virtual Private Gateway, Customer Gateway

![](2020-01-01-18-04-30.png)

- Virtual Private Gateway:
    - VPN concentrator on the AWS side of the VPN connection
    - VGW is created and attached to the VPC from which tou want to create the Site-To-Site connection
    - Possibility to customize the ASN
- Customer Gateway
    - Software application or physical device on customer side of the VPN connection
    - https://docs.aws.amazon.com/vpc/latest/adminguide/Introduction.html#DevicesTested
    - IP Address:
        - Use static, internet-routable IP address for your customer gateway device
        - If behind a CGW behind NAT (with NAT-T), use the public IP address of the NAT