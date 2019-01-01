# Typecasting in Rust

By default, typecasting is not supported in Rust.

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

