---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---

- [[Object Oriented Programming]] languages can't directly map the relationships between objects in the real world into the same model of relationships between them in code.
- [[Child class]]es implement IS-A relationship with base classes - naive statement of [[Object Oriented Programming]].

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
of [[Liskov Substitution Principle]] since the Rectangle is not substitutable by square.

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

This will be refactored in like so:


```csharp
namespace SOLID.LSP.Fixed
{
    public interface IShape
    {
        int CalculateArea();
    }

    public class Rectangle : IShape
    {
        public int Width { get; set; }
        public int Height { get; set; }

        public int CalculateArea() => Width * Height;
    }

    public class Square : IShape
    {
        public int SideLength { get; set; }

        public int CalculateArea() => SideLength * SideLength;
    }

    class EntryPoint
    {
        static void SuperMain(string[] args)
        {
            IShape rect = new Rectangle { Height = 2, Width = 5 };
            int rectArea = rect.CalculateArea();

            Console.WriteLine($"Rectangle Area = {rectArea}");

            ///

            IShape square = new Square() { SideLength = 10 };
            int squareArea = square.CalculateArea();

            Console.WriteLine($"Square Area = {squareArea}");
        }
    }
}
```
