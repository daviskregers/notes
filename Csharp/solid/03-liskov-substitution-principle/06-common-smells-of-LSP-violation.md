# Common smells of LSP violation

- Method throws NotSupportedException
- Emptyy or degenerative implementation
- Downcasts

## Tips
- LSP is often the result of OCP and ISP violations
- If two classes share some logic and they are not substitutable
    - Create new base class
    - Inherit those two classes from a base class
    - Ensure that they are substitutable with the new base class
