# Taking input in Rust

In order to ask user to input a string, you can use something like this:

```rust
use std::io;

fn main() {
    let mut a=String::new();
    println!("Enter a String!");
    io::stdin().read_line(&mut a).expect("Failed");
    println!(" {} ", a);
}
```

The `io::stdin().read_line(&mut a).expect("Failed");` line will read in a line from `stdio` and put it into the `a` variable. By default it will put `Failed`.

In order to use numbers:


```rust
use std::io;

fn main() {
    let mut a=String::new();
    println!("Enter a number!");
    io::stdin().read_line(&mut a).expect("Failed");
    let a:i32 = a.trim().parse().expect("Failed");
    println!(" {} ", a);
}
```

The `.trim()` function will trim the whitespace.

