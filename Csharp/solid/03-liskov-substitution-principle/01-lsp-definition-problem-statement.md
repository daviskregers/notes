# LSP Definition. Problem Statement.

- If S is a subtype of T then objects of type T may be replaced with objects with type S, without breaking the problem.
- The liskov Substitution states that Subtypes must be substitutable for their base types.

Example:
- Class called Client uses an interface B. Classes A and C inherit this interface. Class doesn't care if you pass in the class A or C since all it sees is interface B.

Duck typing in dynamic languages:
- If a bird swims like a duck, it quacks like a duck then I call that bird a duck.

Ways of breaking substitutability:
- Violating a contract
- Violating Covariance\Contravariance
