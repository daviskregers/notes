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

[[Function]] definition consists of a [[function name]], [[return type]], [[parameters]] and the [[function body]].

[[Rust language]] uses [[snake case]] naming style - all letters are in lower case and words are sperated by `_`.

We use `fn` keyword to define a function. Functions can be defined anywhere in the program.

```rust
fn function_name( argument list ) -> (return_type1, return_type2) {
    // statements
}
```

For example

```rust

fn add(a:i32, b:i32) {
    return a +b
}

fn add(a:i32, b:i32) -> i32 {
    return a +b
}

fn sub_add(a:i32, b:i32) -> (i32, i32) {
    return (a-b, a+b)
}

```

The functions can also be nested:

```rust

fn main() {

    fn sub_add(a:i32, b:i32) -> (i32, i32) {
    return (a-b, a+b)
}

    println!("{:?}", sub_add(1,2))

}

```