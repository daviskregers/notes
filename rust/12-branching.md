# Branching in Rust

In branching, we use a conditional statement that runs a different set of statements depending on an expression given.

We can use `If-else` for this:

```rust
fn main() {
    let a = 10;
    if a%2 == 0 {
        println!("Event");
    } else {
        println!("Odd");
    }
}
```

You can also use `Else If` ladder that will execute a collection of `Else If` conditions, provided that previous condition returned `false`.

```rust
if(condition1) {
    // statement
} else if(condition2) {
    // statement - condition1 = false
} else if(condition3) {
    // statement - condition1 = condition2 = false
} else if(condition4) {
    // statement - condition1 = condition2 = condition3 = false
} else {
    // statement - condition1 = condition2 = condition3 = condition4 = false
}
```

```rust
use std::io;

fn main() {

    let mut a=String::new();
    println!("Enter a number!");
    io::stdin().read_line(&mut a).expect("Failed");
    let a:i32 = a.trim().parse().expect("Failed");

    if a% 2 ==0 && a < 0 {
        println!("Number is even and negative")
    } else if a %2 == 0 && a == 0 {
        println!("Number is even and zero")
    } else if a %2 == 0 && a > 0 {
        println!("Number is even and positive")
    } else if a < 0 {
        println!("Number is odd and negative")
    } else {
        println!("Number is odd and positive")
    }

}
```

You can also use `If Else` in assignment operations by using let before the first `if` statement and returning 

```rust
use std::io;

fn main() {

    let mut a=String::new();
    println!("Enter a number!");
    io::stdin().read_line(&mut a).expect("Failed");
    let a:i32 = a.trim().parse().expect("Failed");

    let result = if a% 2 ==0 && a < 0 {
        // .. doing something ..
        "Number is even and negative"
    } else if a %2 == 0 && a == 0 {
        // .. doing something ..
        "Number is even and zero"
    } else if a %2 == 0 && a > 0 {
        // .. doing something ..
        "Number is even and positive"
    } else if a < 0 {
        // .. doing something ..
        "Number is odd and negative"
    } else {
        // .. doing something ..
        "Number is odd and positive"
    };

    println!("{}", result);

}
```

Make sure to leave a semicolor after the last statement.