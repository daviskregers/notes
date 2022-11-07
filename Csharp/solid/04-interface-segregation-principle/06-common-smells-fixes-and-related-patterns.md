# Common smells, fixes and related patterns

- LSP violation smell often indicates a violation of ISP
- Client's code references a class but uses only a small portion of it's API
    - Fat interface -> segregate it
    - Fat interface which is not under your control -> Facade pattern
- Adapter pattern
    - Converts the interface of a class into another interface clients expect.
    - Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

## Adapter example

```csharp
namespace SOLID.ISP
{
    public interface IWideInterface
    {
        void A();
        void B();
        void C();
        void D();
    }

    public interface INarrowInterface
    {
        void A();
        void B();
    }

    class Adapter : INarrowInterface
    {
        private readonly IWideInterface _wide;

        public Adapter(IWideInterface wide)
        {
            _wide = wide;
        }

        public void A()
        {
            _wide.A();
        }

        public void B()
        {
            _wide.B();
        }
    }

    class Client
    {
        private readonly INarrowInterface _narrow;

        public Client(INarrowInterface narrow)
        {
            _narrow = narrow;
        }
    }
}
```

## Tips

- General algorithm of "fixing" fat interfaces
    - Create narrower interface
    - Fat interface inherits from that narrow interface
    - Client uses the narrow interface
- Don't abuse ISP by creating tons of small interfaces
