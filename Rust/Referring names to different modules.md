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

Normally, when using [[Modules in Rust]] we need to do something like this:

```rust

pub mod a {
    pub mod series {
        pub mod of {
            pub fn nested_module() {

            }
        }
    }
}

fn main() {
    a::series::of::nested_module();
}

```

We can fix this by using a `use` keyword.

```rust
use a::series::of::nested_module;
fn main() {
    nested_module();
}
```

We can also use the `use` keyword with enums:

```rust
enum TrafficLight{
    Red, Yellow, Green
}

use TrafficLight::{Red,Yellow}
fn main() {
    let red = Red;
    let yellow = Yellow;
    let green = TrafficLight::Green;
}

```