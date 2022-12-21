---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/open-closed-principle, review]
Review: Hard
---

# Demo of the problem

```csharp
namespace SOLID.OCP.Violation
{
    public class DeviceFinder
    {
        SerialPort port = new SerialPort();
        switch (model)
        {
            case DeviceModel.BillAccepterCashCode:
                {
                    port.BaudRate = 9600;
                    port.Parity = Parity.Even;
                    port.Handshake = Handshake.RequestToSend;
                    return Find(port)
                }
            case DeviceModel.BillDispenserEcdm:
                {
                    port.BaudRate = 4800;
                    port.Parity = Parity.Mark;
                    port.Handshake = Handshake.RequestToSendXonXOff;
                    return Find(port)
                }
            case DeviceModel.CoinAccepterNri:
                {
                    port.BaudRate = 19200;
                    port.Parity = Parity.Odd;
                    port.Handshake = Handshake.XonXOff;
                    return Find(port);
                }
            case DeviceModel.CoinDispenserCube4:
                {
                    port.BaudRate = 9600;
                    port.Parity = Parity.Space;
                    port.Handshake = Handshake.None;
                    return Find(port);
                }
        }
    }
}
```

All this does is calls the find method. If a new case appears, we will need to modify the
program. Often these [[switch case]]s start appearing in other places as well which will make these
modifications even harder.

We can use [[Open-Closed Principle Refactorings]].
