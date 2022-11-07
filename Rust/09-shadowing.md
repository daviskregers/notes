# Shadowing

Using shadowing, you can define a new variable with the same name as a previous variable.

```rust
fn main() {
    let a = 10;
    println!("{}", a);
    let a = 20;
    println!("{}", a);
}
```

Shadowing is different than marking a variable as mutable `mut` - you can also change it's data types:

```rust
fn main() {
    let b:u32 = 128;
    println!("{}", b);
    let b:char = 'c';
    println!("{}", b);
}
```

When using mutuable variables - the data type will be only limited to `u32`.

