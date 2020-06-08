# Common smells of OCP violations

- Many conditional branches with if/else or switch/case statements
- Generally you have 3 approaches to it:
    - Parameterization with delegates. "Chain of responsibility" design pattern.
    - Classic Inheritance or "visitor" design pattern
    - Composition vs Inheritance. "Strategy" design pattern.

