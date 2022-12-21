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

# Operators in Rust

The following operators are supported in rust:

- `+` - [[addition]]
- `-` - [[subtraction]]
- `/` - [[division]]
- `*` - [[multiplication]]
- `%` - [[modulus]]
- `>` - [[greater than]]
- `<` - [[less than]]
- `>=` - [[greater or equal than]]
- `<=` - [[less or equal than]]
- `\==` - [[equal to operation]]
- `\=` - [[assignment operator operator]]
- `&&` - [[and operator]]
- `||` - [[or operator]]
- `!` - [[negate operator]]

The [[operator]]s `++` and `--` are note supported in [[Rust language]]. Instead you can use `+=1` or `-=1` operators. It can be used for `*=` etc as well.

```rust
fn main() {
    println!(" {} ", 1 + 1);
    println!(" {} ", 1 - 1);
    println!(" {} ", 3 * 2);
    println!(" {} ", 4 / 2);
    println!(" {} ", 8 % 3);
    println!(" {} ", 8 > 3);
    println!(" {} ", 8 < 3);
    println!(" {} ", 8 >= 3);
    println!(" {} ", 8 <= 3);
    println!(" {} ", 8 == 8);
    println!(" {} ", true && false);
    println!(" {} ", true || false);
    println!(" {} ", true && !false);
}
```

```
 ✘ davis@davis-arch  ~/projects/rust  ./5_operators 
 2 
 0 
 6 
 2 
 2 
 true 
 false 
 true 
 false 
 true 
 false 
 true 
 true 
```