# IoC and DI definitions

## Inversion of Control (IoC)
- IoC reflects the model of relationships between a caller and a callee.
- A classic flow of control implies that a client has a full control over the environment and sequence of calls to library methods.
- IoC implies that a callee takes control over some calls between caller and callee. (callbacks is the simplest form)
- Frameworks rule the client's code.

## Dependency Inversion Principle

- DIP is a detailed version of IoC
- Concretizes that "High-level modules should not depend on low level modules"

## Dependency Injection (DI)

- Dependency Injection (DI) is a set of software design principles and patterns that enable us to develop loosely coupled code.

## IoC and DI

- IoC can exist without DI
- The main way to perform the inversion of control is to apply DI techniques
