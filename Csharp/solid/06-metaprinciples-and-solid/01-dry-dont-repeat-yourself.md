# DRY - Don't repeat yourself

A substantial number of bugs in software are caused by repetitive code.

Every piece of knowledge must have a single unambiguous representation in the system.

## Common violations of DRY

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

## Duplicate logic in multiple locations
## Repeated "if-then" logic or multiple switch-cases scattered thoughout the code base.

Bad:
```csharp
public enum Shape
{
    Circle,
    Rectangle,
    Square,
    Hexagon
}

public class Visualizer
{
    public void Draw(Shape shape)
    {
        switch(shape)
        {
            case Shape.Circle:
                break;
            case Shape.Hexagon:
                break;
            case Shape.Rectangle:
                break;
            case Shape.Square:
                break;
        }
    }

    public decimal CalculateArea(Shape shape)
    {
        ... switch case
    }
}
```


Good:
```csharp
abstract class Shape
{
    abstract void Draw();
    abstract decimal CalculateArea();
}

public class Rectangle : Shape
{
    public override void Draw()
    {
    }

    public override decimal CalculateArea()
    {
    }
}

public class Circle : Shape
{
    public override void Draw()
    {
    }

    public override decimal CalculateArea()
    {
    }
}
```
