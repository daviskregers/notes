# Operators in Rust

The following operators are supported in rust:

- `+` - addition
- `-` - subtraction
- `/` - division
- `*` - multiplication
- `%` - modulus
- `>` - greater than
- `<` - less than
- `>=` - greater or equal than
- `<=` - less or equal than
- `==` - equal to
- `=` - assignment operator
- `&&` - and
- `||` - or
- `!` - negate

The operators `++` and `--` are note supported in Rust. Instead you can use `+=1` or `-=1` operators. It can be used for `*=` etc as well.

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