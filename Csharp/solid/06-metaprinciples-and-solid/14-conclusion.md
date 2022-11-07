# Conclusion

- DRY states: "every piece of knowledge must have a single, unambigous representation in the system"
    - Magic strings or values
    - Duplicated logic in multiple locations
    - Repeated if-then logic or multiple switch-case statements
- KISS - simplicity should be a key goal in design, decomposition is a key
- YAGNI - don't add functionality until deemed necessary
- SoC - separate different concerns from each other
- SQS - every method should be either a command or query
- LoD - Each unit should have only limited knowledge about other units. Only units closely related to the current unit.
- PoLA - component should behave as it is expected by clients.
- Encapsulation is intended to protect invariants. Information hiding is one of the ways to achieve proper encapsulation.
- Achieve balance between complexity and simplicity applying the reused abstraction principle
- OCP beats YAGNI in case of public API
- YAGNI beats OCP in case of private API
- SRP and ISP don't contradict with each other
- Architecture is the agreement between group of people regarding the importance of system components
- Software design concerns implementation - classes, interfaces
