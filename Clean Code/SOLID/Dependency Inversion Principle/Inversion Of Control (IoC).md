---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

- IoC reflects the model of relationships between a [[caller]] and a [[callee]].
- A classic [[flow of control]] implies that a client has a full control over the [[environment]] and sequence of calls to library methods.
- IoC implies that a callee takes control over some calls between caller and callee. (callbacks is the simplest form)
- Frameworks rule the client's code.

IoC can exist without [[Dependency Injection]], buy the main way to perform the inversion of control is to apply [[Dependency Injection]] techniques.