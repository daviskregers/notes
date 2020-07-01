# Principle of least astonishment

A component of a system should behave in a manner consistent with how users of that component are likely expect it to behave.

Following principles and techniques are based on the principle of least astonishment:
- Fault-Safe API
- Command-Query Separation
- Immutability
- Design by Contract

Works fine:
```csharp
reporting.PrintReportA();
reporting.PrintReportB();
```

Fails in runtime. Astonishment.
```csharp
reporting.PrintReportB();
reporting.PrintReportA();
```
---

Java stack exposes:
- Push
- Pop
- Add - Where the item will be added?

```csharp
var array = new string[10];
var list = array as IList<string>; // this works
list.Add("foo"); // exception saying it's not supported
```
