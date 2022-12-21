---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---

Assuming the type A can be cast to type B, type X is covariant in case X\<A\> can be cast to X\<B\>. For example IBar\<T\> is covariant to T, if the following is true:.

```csharp
IBar<string> s = ...;
IBar<object> o = s; // compiles

class Animal {}
class Dog : Animal {}
class Cat : Animal {}

public class Stack<T>
{
    int position;
    T[] data = new T[100];
    public void Push(T val) { data[position++] = val; }
    public T Pop() { return data[--position]; }
}

Stack<Dog> dogs = new Stack<Dog>();
Stack<Animal> animals = dogs; // compilation error

// for preventing such code:
animals.Push(new Cat()); // adding cat to dogs.

Dog[] dogs = new Dog[10];
Animal[] animals = dogs;
animals[0] = new Cat(); // runtime exception will occur
```