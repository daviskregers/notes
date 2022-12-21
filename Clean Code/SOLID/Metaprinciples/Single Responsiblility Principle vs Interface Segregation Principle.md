---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

- [[Single Responsibility Principle]] implies that a class should have only one reason to change. [[Interface Segregation Principle]] at the same time tells that clients should not depend on things they do not need.
- [[Interface Segregation Principle]] and [[Single Responsibility Principle]] are different views on the same idea. SRP is more focused on the designer-side point of view, while ISP is more focused on the client-side point-of-view.

In this example, it would be odd to separate these these responsibilities for SRP,
but in ISP it makes sense to do so to hide unneeded things from clients.

```csharp
class Persister : IReader, IWriter {
    public byte[] Read(string file) {}
    public void Write(byte[] content) {}
}

interface IReader {
    byte[] Read(string file);
}

interface IWriter {
    void Write(byte[] content);
}
```
