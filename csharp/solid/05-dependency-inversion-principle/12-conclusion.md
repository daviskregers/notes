# Conclusion

- DIP implies that high-level policies should not depend on low-level details
- Two major types of dependencies: stable and unstable (or volatile)
    - Unstable dependencies are those to which we want to apply the inversion of control
- What IoC and DI are and how they are related to the DIP and to each other
- 3 techniques of DI
    - Constructor injection, should be used 95% of the cases
    - Property and method injection
    - Method injection
- Adhering to DIP leads to a plugin architecture which is known as the "Ports and Adapters" architecture.
- There should be a single place which knows everything about application dependencies and their relationships and this is the `Main`.
- Manual dependency injection may become tedious. That's why IoC containers exist, they help to simplify DI in difficult cases.
