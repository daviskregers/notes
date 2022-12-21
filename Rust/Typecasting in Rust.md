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


By default, [[typecasting]] is not supported in [[Rust]].

```rust
fn main() {
    let a:i32 = 10;
    let b:i64 = a;
}
```

Will throw an error `mismatched types`.

This can be fixed by using something like this:

```rust
fn main() {
    let a:i32 = 10;
    let b:i64 = a as i64 + 10;
}
```

or 

```rust
fn main() {
    let a:i32 = 10;
    let b:i64 = a.into() + 10;
}
```

