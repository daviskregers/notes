# Route 53 - 3rd Party Domains

- You buy or register your domain name iwth a Domain Registrar typically by paying annual charges (e.g. GoDaddy, Amazon Registrar Inc, ...)
- The Domain Registrar usually provides you with a DNS service to manage your DNS records
- Buy you can use another DNS service to manage your DNS records
- Example: purchase the domain from GoDaddy and use Route 53 to manage your DNS records

---

- If you buy your domain on a 3rd Party Registrar, you can still use Route 53 as the DNS Service Provider

1. Create a Hosted Zone in Route 53
2. Update NS Records on 3rd Party website to use Route 53 Name Servers

- Domain Registrar != DNS Service
- But every Domain Registrar usually comes with some DNS features