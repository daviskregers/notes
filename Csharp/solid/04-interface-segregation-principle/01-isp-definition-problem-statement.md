# ISP Definition. Problem statement.

- "interface" is a reserved keyword in C# which allows to declare a non-implemantable type consisting of member signatures
- Defines an API
- Public API of a class is and interface

Definition:
- ISP states that Clients should not be forced to depend on methods they do not use. Prefer small, cohesive interfaces.

 ## Historical Background
 - First public formulation belongs to Uncle Bob
 - Uncle Bob applied ISP working for Xerox
 - That was a printing system
 - A single job task contained fat list of tasks even though there was no use for them.

- ISP violations result in classes that depend on things they do not need, increasing coupling and reducing maintainability.
