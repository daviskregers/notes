---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

### Magic strings or any other magic values

Bad:
```csharp
int responseCode = GetDeviceResponse();
if (responseCode == 188) {
    ...
}
```

Good (this can be reused elsewhere):
```csharp
const int NoConnection = 188;
int responseCode = GetDeviceResponse();
if (responseCode == NoConnection) {
    ...
}
```



---

Bad:

```csharp
public class MagicValues
{
    public void AcceptCard()
    {
        var d = new Device();
        d.SendCommand(1);
        d.SendCommand(2);
        d.SendCommand(9);
    }

    public void DispenseCard()
    {
        var d = new Device();
        d.SendCommand(1);
        d.SendCommand(3);
        d.SendCommand(9);
    }
}
```

Without magic values:

```csharp
public class NoMagic
{
    private const int Initialize = 1;
    private const int Terminate = 9;

    public void AcceptCard() {
        var d = new Device();
        d.SendCommand(Initialize);
        d.SendCommand(2);
        d.SendCommand(Terminate);
    }

    public void DispenseCard()
    {
        var d = new Device();
        d.SendCommand(Initialize);
        d.SendCommand(3);
        d.SendCommand(Terminate);
    }
}
```

Good:
```csharp
public class NoDuplicateLogic {
    private const int Initialize = 1;
    private const int Terminate = 9;

    public void AcceptCard() {
        ExecuteCommand(2);
    }

    public void DispenseCard()
    {
        ExecuteCommand(3);
    }

    private void ExecuteCommand(byte command)
    {
        var d = new Device();
        d.SendCommand(Initialize);
        d.SendCommand(command);
        d.SendCommand(Terminate);
    }
}
```
