# Demo of the problem

- OOP can't directly map the relationships between objects in the real world into the same model of relationships between them in code.
- Child classes implement IS-A relationship with base classes - naive statement of OOP.

## The problem

- Implement rectangle and square.
- Obviously Square implements Rectangle.

```csharp
namespace SOLID.LSP.Violation
{
    public class Rectangle
    {
        public int Width { get; set; }
        public int Height { get; set; }
    }

    public class Square : Rectangle
    {

    }

    public class AreaCalculator
    {
        public static int CalcSquare(Square square) => square.Height * square.Height;
        public static int CalcRectangle(Rectangle square) => square.Height * square.Width;
    }

    class EntryPoint
    {
        static void SuperMain(string[] args)
        {
            Rectangle rect = new Rectangle() { Width = 2, Height = 5 };
            int rectArea = AreaCalculator.CalcRectangle(rect);

            Console.WriteLine($"Rectangle Area = {rectArea}");

            Rectangle square = new Square { Height = 2, Width = 10 };

            int squareArea = AreaCalculator.CalcRectangle(square);
            Console.WriteLine($"Square Area = {squareArea}");
        }
    }
}
```

The problem is that we can specify different height and with for a square, therefore the
you would need to implement additional business logic for that and that solution is a violation
of LSP since the Rectangle is not substitutable by square.

```csharp
public static int CalcArea(Rectangle rect)
{
    if (rect is Square)
    {
        return rect.Height * rect.Height;
    }
    return rect.Height * rect.Width;
}
```
