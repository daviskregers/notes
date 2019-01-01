# Mutability and intro into strings

By default variables in immutable - once the value is bound to a name, you can't change that value.

```rust
fn main() {
    let a = 10;
    a = 20;
    println!("{}", a)
}
```

When compiling this program, it will throw an error saying `error: re-assignment of immutable variable`.

However, sometimes the mutability can become very useful, it can be added by specifying `mut` keyword:

```rust
fn main() {
    let mut a = 10;
    a = 20;
    println!("{}", a)
}
```

There is also a variable type of Constant. They are bound to a name and are not allowed to change - you cannot add the `mut` keyword.

Constants can be defined using `const` keyword, data type must be annotated. Can be defined in any scope, including the global scope. 

By convention, the constant names must be defined in all caps.

```rust
const MAX:u8 = 132;
fn main() {
    let mut a = 10;
    a = 20;
    println!("{} {}", a, MAX)
}
```