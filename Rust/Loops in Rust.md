---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust/testing, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

In [[loops]] you repeat a set of operations until a certain given condition is no longer met.

In [[Rust language]] there are 3 types of loops - `loop`, `while` and `for` loops.

```rust
fn main() {
    
    let mut n =0;

    loop {
        if n < 5 {
            println!("{}", n);
            n += 1;
        } else {
            break;
        }
    }

    while n <= 10 {
        println!("{}", n);
        n += 1;
    }

    for n in 10 .. 21 {
        println!("{}", n);
    }

}
```

The [[loop]] is a simple loop, [[breaking condition]] must be explicitly given. Best when you want to set up an [[infinite loop]].

The [[while loop]] is useful for a program to evaluate a [[condition]] within a [[loop]].

The [[for loop]] is used to [[iterate]] over a [[collection]] of items. 

The rust's [[for loop]] is faster than the [[while loop]] because the compiler adds extra [[runtime code]] to perform [[conditional checks]] on every element on every [[iteration]].
