---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---

[[Liskov Substitution Princple Common Smells]]

![[Covariance]]

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
