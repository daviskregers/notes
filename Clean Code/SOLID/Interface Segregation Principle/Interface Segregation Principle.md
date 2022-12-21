---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/interface-segregation-principle, review]
Review: Hard
---

Interface Segregation Principle states that Clients should not be forced to depend on methods they do not use. Prefer small, [[cohesive]] [[interface]]s.

## Historical Background

- First public formulation belongs to [[Uncle Bob]]
- Uncle Bob applied Interface Segregation Principle working for Xerox
- That was a [[printing system]]
- A single job task contained fat list of tasks even though there was no use for them.

- [[Interface Segregation Principle Violations]] result in [[class]]es that depend on things they do not need, increasing [[coupling]] and reducing [[maintainability]].

[[Interface Segregation Principle Demo]]
[[Interface Segregation Principle Refactorings]]
[[Interface Segregation Principle Common smells and Related Design Patterns]]

[[Single Responsiblility Principle vs Interface Segregation Principle]]