---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc, development/networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# Egress Only Internet Gateway

- Egress only [[Internet Gateway & Route tables]] if for [[IPv6]] only
- Similar function as a [[NAT]], but a NAT is for [[IPv4]]
- Good to know: [[IPV6]] are all public addresses
- Therefore all our instances with [[IPv6]] are publicly accessible
- Egress only Internet Gateway gives our [[IPv6]] instances access to the internet, but they won't be directly reachable by the internet
- After creating an Egress Only Internet Gateway, edit the [[Internet Gateway & Route tables]]

