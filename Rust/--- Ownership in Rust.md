---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

# Ownership in Rust

[[Rust language]]'s most unique feature is [[ownership]] feature. It enables Rust to make [[memory safety guarantees]] without needing a [[garbage collector]].

[[Memory Allocation]]

## Ownership rules

- Each value in Rust has a [[variable]] that is it's owner.
- There can only be one owner at a time, cannot point at one memory location.
- When the owner goes out of the [[scope]], the value will be dropped.

## Memory and allocation

- [[String]] type, in order to support a [[mutable]], [[growable]] piece of text, we need to allocate an amount of memory on the [[Heap]], unknown at the [[compile time]], to hold the contents.
  - The [[memory]] must be requested from the [[operating system]] at [[runtime]]
  - We need a way of returning this memory to the [[operating system]] when we're done working with it.
- In languages with a [[garbage collector]], the [[garbage collector]] keeps track and cleans up memory that isn't being used anymore. We don't need to think about it.
- Without the [[garbage collector]], it is our responsibility to identify when memory is no longer being used and explicitly [[call to return]] it.
- [[Rust language]] takes a different path - the memory is [[automatically returned]] once the variable that owns it goes out of scope.

```rust
fn main() {
    let s = String::from("hello"); 
    ...
}
```
- When a variable goes out of scope, Rust calls a special function called [[drop]]. This function is called each time a the closing bracket.

So, when using something like this

```rust
fn main() {
    let s1 = String::from("Hello");
    let s2 = s1;
    println!("{} {}", s1, s2);
}
```

It will raise an error since both of the variables point to the same location in memory. 

It can be fixed by deep copying the heap data of the String:

```rust
fn main() {
    let s1 = String::from("Hello");
    let s2 = s1.clone();
    println!("{} {}", s1, s2);
}
```

The same example for the stack will work, since the size is known at the compile time.

```rust
fn main() {
    let x = 5;
    let y = x;
    println!("{} {}", x, y);
}
```

## Ownership and functions

The semantics for passing a value to a function are similar to those for assigning a value to a variable.

Passing a variable to a function will move or copy, just as assignment does.

So, when using something like this:

```rust
def main() {
    let s = String::from("Hello");
    take(s);
    println!("{}", s);
}

fn take(s1: String) {
    println!("{}", s1)
}
```

An error will be thrown since the `take()` function transfers the ownership to the `s1` variable and the `println!("{}", s);` accesses data that it has no longer ownership to.

Returning values can also transfer ownership. 


```rust
def main() {
    let mut s = String::from("Hello");
    s = take(s);
    println!("{}", s);
}

fn take(s1: String) -> String {
    println!("{}", s1)
    s1
}
```

Now there won't be any errors thrown.

## References and borrowing

Usiung references, we can reger a value without taking ownership of it.

`&` ampersands are references.

```rust
let s1 = String::from("hello");
print(&s1);
```

The print function will not get the ownership of the variable.

We don't drop what the reference points to when it goes out of scope because we don't have ownership. So, when we use a function that accepts a reference. When the scope ends - only the reference is dropped not the data it points to.

References as function parameters are known as borrowing.

Using references, we cannot modify the underlying values it points to.

In order to allow it to modify the data, we must explicitly specify a mutable reference:

```rust
print(&mut s);
```

```rust
fn main() {
    let mut s = String::from("Hello");
    print(&mut s);
    println!("{}", s)
}

fn print(s1: &mut String) {
    println!("{}", s1);
    s1.push_str("World")
}
```

## Rules of references

- You can create any number of immutable references
- You can create only one mutable references in a scope.
- You cannot have an immutable reference if your scope uses a mutable reference.

## Data race

- A data race is similar to a race condition and happens when these 3 behaviours occur:
  - Two or more pointers access the same data at the same time.
  - At least one of the pointers is being used to write the data.
  - There's no mechanism being used to synchronize access to the data.
- Data races cause undefined behaviour and can be difficult to diagnose when you're trying to track them down at runtime. Rust prevents this problem from happening because it won't even compile code with data races.

## Dangling references

Pointer that references a location in memory that doesn't exist is called a dangling reference.

```rust
fn main() {
    let s = dangle();
}

fn dangle() -> &String {
    String d = String::from("hello");
    &d
} // d goes out of scope here
```

This code will not compile in rust, an error will be thrown that `this function's return type contains a borrowed value, but there is no value for it to be borrowed from` since the value is dropped at the end of the scope.

## Slices in Rust

Slices let you reference a contiguous sequence of elements.

```rust
let a = String::from("Hello World");
let r1 = &a[0..5];
let r2 = &a[0..=5];
let r3 = &a[ .. 5];
let r4 = &a[0 ..];
let r5 = &a[..];
```

