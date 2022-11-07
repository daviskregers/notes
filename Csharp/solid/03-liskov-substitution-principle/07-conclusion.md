# Conclusion

- The Liskov Substitution Principle states that Subtypes must be substitutable for their base types.
- Do not violate a Contract by either strenghtening preconditions or weakening postconditions;
- Do not violate Covariance/Contravariance, explicitly mark the generic parameters by "in" and "out" keyword if possible.

## Common smells
- Method throws NotSupportedException
- Empty implementations or stubs
- Switch-case statemen with checks of the actual type of an argument.
- Downcasts
