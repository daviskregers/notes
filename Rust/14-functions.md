# Functions in Rust

Function definition consists of a function name, return type, parameters and the function body.

Rust uses snake case naming style - all letters are in lower case and words are sperated by `_`.

We use `fn` keyword to define a function. Functions can be defined anywhere in the program.

```rust
fn function_name( argument list ) -> (return_type1, return_type2) {
    // statements
}
```

For example

```rust

fn add(a:i32, b:i32) {
    return a +b
}

fn add(a:i32, b:i32) -> i32 {
    return a +b
}

fn sub_add(a:i32, b:i32) -> (i32, i32) {
    return (a-b, a+b)
}

```

The functions can also be nested:

```rust

fn main() {

    fn sub_add(a:i32, b:i32) -> (i32, i32) {
    return (a-b, a+b)
}

    println!("{:?}", sub_add(1,2))

}

```