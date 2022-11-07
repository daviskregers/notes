# Refactoring to a better design

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
