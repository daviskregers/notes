# Strings

Rust has only one string type in the core language, which is string slice `&str`.

The String type is provided by Rust's standard library rather than coded into the core language.

It is growable, mutable and UTF-8 encoded type.

The `growable` means that you can add another string to it, for example adding a string "World" to "Hello, ". This cannot be done when using the string slices.

The `mutable` means - you can mutate the memory location. This cannot be done when using the string slices.

```rust
fn main() {
    let mut a = String::new();
    a = String::from("Hello");
    a.push_str(", World!");
    println!(" {} ", a)
}
```