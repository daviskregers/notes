---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/design-pattern, review]
Review: Hard
---

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
