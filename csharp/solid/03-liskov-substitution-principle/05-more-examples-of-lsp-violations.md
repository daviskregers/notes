# More Examples of LSP Violations

## Covariance

Assuming the type A can be cast to type B, type X is covariant in case X<A> can be cast to X<B>.
For example, IBar<T> is covariant to T, if the following is true:

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

---

Dog[] dogs = new Dog[10];
Animal[] animals = dogs;
animals[0] = new Cat(); // runtime exception will occur
```

## Variance in C#

Starting from C# 4, generic interfaces allow variance though special keywords "in" and "out".
Generic classes at the same time don't allow variance.

The "out" keyword guarantees that inside the implementation of that interface, a generic parameter can only be used in the return statments.

```csharp
interface IPoppable<out T< { T Pop(); }
```

Compiles and absolutely correct:

```csharp
var dogs = new Stack<Dog>();
dogs.Push(new Dog());
IPoppable<Animal> animals = dogs; // allowed
```

---

The "in" keyword guarantees that inside the implementation of that interface, a generic parameter can only be used as the input.

```csharp
interface IPushable<in T> { void Push(T val); }
```

Compiles and absolutely correct:

```csharp
IPushable<Animal> animals = new Stack<Animal>();
IPushable<Cat> cats = animals; // allowed
cats.Push(new Cat());
```

## Downcasts is a smell

```csharp
void PayBonus(Person p)
{
    Customer c = (Customer)p; // downcast
    // or
    if (p is Person) {
        Customer c = (Customer)p;
    }
}

## Downcasts are not always the smell

Downcasts are allowed if we're absolutely sure about the type you're about to
downcast to.

```csharp
public void PayCashBack(int customerId, decimal amount)
{
   Customer c = repository.GetCustomer(customerId);
   var pv = c as PrivilegedCustomer;
   if (pc != null {
        pc.AddMoneyToAccount(amount);
   }
   else {
        throw new ArgumentException("PayCashback on a regular customer");
   }
}
```
