# Route 53 Overview

- The Amazon Route 53 is a highly available, scalable, fully managed and authoritative DNS.
    - The authoritative means that the customer (you) can update the DNS records.
- Route 53 is also a Domain Registrar so you can register your domain names there as well.
- Provides an ability to check the health of your resources
- The only AWS service which provides 100% availability SLA (service level agreement)

## Route 53 - Records

- How you want to route traffic for a domain
- Each record contains:
    - Domain/subdomain name - e.g. example.com
    - Record Type - e.g. A or AAAA
    - Value - e.g. 12.34.56.78
    - Routing Policy - how Route 53 responds to queries
    - TTL - amount of time the record is cached at resolvers
- Route 53 supports the following DNS record types
    - (must know) A / AAAA / CNAME / NS
    - (advanced) CAA / DS / MX / NAPTR / PTR / SOA / TXT / SPF / SRV

## Route 53 - Record Types

- A - maps a hostname to IPv4
- AAAA - maps a hostname to IPv6
- CNAME - maps a hostname to another hostname
    - The target is a domain name which must have an A or AAAA record
    - Can't create a CNAME record for the top node of a DNS namespace (Zone Apex)
        - Example: you can't create one for example.com but you can create for www.example.com
- NS - Name Servers for the Hosted Zone
    - Control how traffic is routed for a domain

## Route 53 - Hosted Zones

- A container for records that define how to route traffic to a domain and its subdomains
    - Public Hosted Zones - contains records that specify how to route traffic on the internet (public domain names)
        - application1.mypublicdomain.com
    - Private Hosted Zones - contain records that specify how you route traffic within one or more VPCs (private domain names)
        - aplication1.comany.internal

- You pay $0.50 per month per hosted zone
