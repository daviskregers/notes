# OCP Related Patterns

## Template Method
- There is an algorithm but small parts of the algorithm may vary.
- It defines the skeleton of an algorithm in an operation, deferring some steps to subclasses.
- Template method lets subclasses redefine certains steps of an algorithm without changing the algorithm's structure.

```csharp
namespace SOLID.OCP
{
    public abstract class PaymentProcessor
    {
        public void ProcessTransaction()
        {
            WithdrawMoney();
            CalculateBonus();
            SendGreetings();
        }
        protected abstract void WithdrawMoney();
        protected abstract void CalculateBonus();
        protected abstract void SendGreetings();
    }

    public class OnlineProcessor : PaymentProcessor
    {
        protected override void WithdrawMoney() {}
        protected override void CalculateBonus() {}
        protected override void SendGreetings() {}
    }

    public class PosTerminalProcessor : PaymentProcessor
    {
        protected override void WithdrawMoney() {}
        protected override void CalculateBonus() {}
        protected override void SendGreetings() {}
    }
}
```

## Strategy

- The strategy enables an algorithm's behavior to be selected at runtime.
- The strategy pattern:
    - defines a family of algorithms
    - encapsulates each algorithm
    - makes the algorithms interchangeable within that family

## Interfaces

- Interfaces can't be easilyt changed without breaking existing clients
- Interfaces are easily extendable by clients

### Corollaries:
- An interface is suppler from the client's perspective: any class can implement as many interfaces as it wants to.
- An interface is more rigid from the developer's perspective: it can't be easily changed and it does not support any kind of reusability

## Abstract classes

- Supports reusability
- Supports encapsulation
- Can be extended easily without breaking existing clients

## Corollaries:
- An abstract class is supple from the developer's perspective
- An abstract class is rigid from the client's perspective

## Interfaces vs Abstract Classes

- Use abstract classes for building internal APIs
- Use interfaces for providing external points of extension

### Visitor pattern

```csharp
namespace SOLID.OCP.Refactored
{
    public class BillDispenserEcdm : Device, IDevice
    {
        public BillDispenserEcdm()
        {
            Port = new SerialPort
            {
                BaudRate = 4800,
                Parity = Parity.Mark,
                Handshake = Handshake.RequestToSendXOnXOff
            };
        }

        public SerialPort Port { get; }

        public string Find()
        {
            foreach (string portName in SerialPort.GetPortNames())
            {
                Port.Write("Special code");
                if (Port.ReadByte == 120)
                    return portName;
            }
            return null;
        }

        public override void Accept(IDeviceVisitor visitor)
        {
            visitor.Visit(this);
        }
    }

    public interface IDeviceVisitor
    {
        void Visit(BillDispenserEcdm billDispenser);
        void Visit(CoinDispenserCube4 coinDispenser);
    }

    public abstract class Device
    {
        public abstract void Accept(IDeviceVisitor visitor);
    }

    public class CloseCommandVisitor : IDeviceVisitor
    {
        public void Visit(BillDispenserEcdm billDispenser)
        {
            SerialPort port = billDispenser.Port;
            port.Write(new byte[] { 0x03 }, 0, 1);
        }

        public void Visit(CoinDispenserCube4 coinDispenser)
        {
            SerialPort port = coinDispenser.Port;
            port.Write(new byte[] { 0x12 }, 0, 1);
        }
    }

    public static class DeviceEx
    {
        public static void Close(this Device device)
        {
            var visitor = new CloseCommandVisitor();
            device.Accept(visitor);
        }
    }

    public class Client
    {
        void Logic()
        {
            var device = new BillDispenserEcdm();
            device.Close();
        }
    }
}
```
