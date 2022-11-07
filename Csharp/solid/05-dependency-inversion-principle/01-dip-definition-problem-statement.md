# Dependency Inversion Principle. Problem Statement.

- DIP is all about decoupling
    - Coupling indicates how dependent modules are on the inner working of each other.
    - Low coupling is often a sign of a well-structured computer system and a good design,and when combined with high cohesion, supports the general goals of high readability and maintainability.
- DIP is applicable both at the source code and binary level
- High-level modules should not depend on low-level modules. Both should depend on abstractions.
- Abstractions should not depend on details. Details should depend on abstractions.

```
Would you solder a lamp directly to the electrical outlet on your wall?
```

- You would only be able to use that socket for your lamp since they are tightly coupled.
- To fix the issue, we need to come up with a standard plug - then it can be plugged in the socket.

