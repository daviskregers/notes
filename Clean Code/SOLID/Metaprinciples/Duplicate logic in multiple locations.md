---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

Repeated "if-then" logic or multiple [[switch case]]s scattered though-out the [[code base]].

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
