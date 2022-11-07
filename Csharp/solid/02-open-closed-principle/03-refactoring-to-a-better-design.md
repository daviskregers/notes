# Refactoring to a better design

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace SOLID.OCP.Refactored
{
    public interface IDevice
    {
        string Find();
    }

    public class BillDispenserEcdm : IDevice
    {
        public string Find()
        {
            SerialPort port = new SerialPort
            {
                BaudRate = 4800,
                Parity = Parity.Mark,
                Handshake = Handshake.RequestToSendXOnXOff
            };

            foreach(string portName in SerialPort.GetPortNames())
            {
                // test if device can be connected
                port.Write("special code");
                if (port.ReadByte() == 120)
                    return portName;
            }
            return null;
    }

    public class CoinDispenserCube4 : IDevice
    {
        public string Find()
        {
            SerialPort port = new SerialPort
            {
                BaudRate = 9600,
                Parity = Parity.Space,
                Handshake = Handshake.None
            };

            foreach (string portName in SerialPort.GetPortNames())
            {
                port.Write("Special code")
                if (port.ReadByte == 0)
                    return portName;
            }
            return null;
        }
    }

    public class DeviceFinder
    {
        private readonly IDevice _device;

        public DeviceFinder(IDevice device)
        {
            _device = device;
        }

        public string Find()
        {
            return _device.Find();
        }
    }
}
```


- We can't achieve a super-supple design which allows to introduce any possible features.

## Development Metodologies

- Waterfall
    - Try to foresee all the possible details
- Agile
    - Iterative development process with high involvement of a customer
