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

A [[module]] is a collection of methods, it is defined by a keyword `mod`.

```rust

mod client {
    fn connect() {}
}

mod network {
    fn connect() {}

    mod server {
        fn connect() {}
    }

}

```

You can also move the modules into separate files:

```rust
mod client;
```

and client.rs:

```rust 
fn connect() {}
```

![[ Controlling Visibility ]]

![[Referring names to different modules]]

