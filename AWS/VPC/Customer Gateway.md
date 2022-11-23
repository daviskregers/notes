---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/vpc/vpn, networking, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

## Customer Gateway

- [[Software application]] or [[physical device]] on [[customer side]] of the [[VPN connection]]
- https://docs.aws.amazon.com/vpc/latest/adminguide/Introduction.html#DevicesTested
- [[IP Address]]:
	- Use [[static]], internet-routable [[IP address]] for your [[customer gateway device]]
	- If behind a CGW behind [[NAT]] (with NAT-T), use the [[public IP]] address of the [[NAT]]