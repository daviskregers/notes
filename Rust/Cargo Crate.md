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

A crate is a [[package]] of rust code [https://crates.io/](https://crates.io/) with a [[binary]] or [[library]] type.

The crates / dependencies can be added to the `Cargo.toml' file:

```
[dependencies]
rand = "0.5.0"
```

Now, when running `cargo build`, it will automatically download the [[Dependency]].

Crates can be updated using the `cargo update`.

to include the crate in the code you can use

```
extern crate rand;
use rand::Rng;

fn main() {

}
```