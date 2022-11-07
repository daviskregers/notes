# SRP and ISP. What's the difference?

- SRP implies that a class should have only one reason to change. ISP at the same time tells that clients should not depend on things they do not need.
- ISP and SRP are different views on the same idea. SRP is more focused on the designer-side point of view, while ISP is more focused on the client-side point-of-view.

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
