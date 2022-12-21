---
Created: 2022-12-01 17:58:15
Modified: Wednesday 30th November 2022 09:28:09
Type: article
Source: https://en.wikipedia.org/wiki/Service-oriented_architecture
Tags: [development/architecture/soa, review]
Review: Hard
---

Service Consumer locates entries in the [[Service Broker]] using various find operations and then binds to the [[Service Provider]] in order to invoke one of its web services. 

Whichever service the service-consumers needs, they have to take it into the brokers, bind it with respective service and then use it. They can access multiple services if the service provides multiple services.

The service consumer–provider relationship is governed by a [[Service Contract]] which has a business part, a functional part and a technical part.

[[Service composition patterns]] have two broad, high-level architectural styles:
- [[choreography]]
- [[orchestration]]

Lower level enterprise integration patterns that are not bound to a particular architectural style continue to be relevant and eligible in [[Service-Oriented Architecture (SOA)]] design.