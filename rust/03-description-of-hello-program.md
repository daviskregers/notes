# Description of the Hello World program

Previously we made a following "Hello World" program:

```rust
fn main() {
    println!("Hello World");
}
```

The keyword `fn` is for declaring functions, just like in C language - it will look for the `main` function to execute the program. 

If we change the `main` to `hello`, an error will be thrown:

```bash
davis@davis-arch  ~/projects/rust  rustc hello.rs
error[E0601]: `main` function not found in crate `hello`
  |
  = note: consider adding a `main` function to `hello.rs`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0601`.
```

The `println` function prints a line in the terminal screen. You can also use placeholders in it.

```rust
fn main() {
    println!("Hello, {}! {}", "World", 2);
}
```

```
davis@davis-arch  ~/projects/rust  ./hello 
Hello, World! 2
```

