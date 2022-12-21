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

# Description of the Hello World program

Previously we made a following "Hello World" program:

```rust
fn main() {
    println!("Hello World");
}
```

The keyword `fn` is for declaring [[function]]s, just like in [[C language]] - it will look for the `main` [[function]] to execute the program. 

If we change the `main` to `hello`, an [[error]] will be thrown:

```bash
davis@davis-arch  ~/projects/rust  rustc hello.rs
error[E0601]: `main` function not found in crate `hello`
  |
  = note: consider adding a `main` function to `hello.rs`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0601`.
```

The `println` [[function]] prints a line in the [[terminal]] screen. You can also use [[placeholders]] in it.

```rust
fn main() {
    println!("Hello, {}! {}", "World", 2);
}
```

```
davis@davis-arch  ~/projects/rust  ./hello 
Hello, World! 2
```

