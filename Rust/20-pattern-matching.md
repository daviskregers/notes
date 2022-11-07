# Pattern matching

## Match Control Flow Operator

Match allows you to compare a value against a series of patterns and then execute code based on which pattern matches.

```rust

enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter
}

fn value_in_cents(c: Coin) -> u32 {
    match c {
        Coin::Penny => 1,
        Coin::Nickel => 5,
        Coin::Dime => 10,
        Coin::Quarter => 25,
    }
}

```

```rust
fn value_in_cents(c: Coin) {
    match c {
        Coin::Penny => {
            println!("This is a Penny and it's value is 1.");
        },
        Coin::Nickel => {
            println!("This is a Nickel and it's value is 5.");
        },
        Coin::Dime => {
            println!("This is a Dime and it's value is 10.");
        },
        Coin::Quarter => {
            println!("This is a Quarter and it's value is 25.");
        }
    }
}
```

## Patterns that binds to value

```rust

enum Coin {
    Penny,
    Nickel,
    Dime,
    Quarter(State)
}

#[derive(Debug)]
enum State {
    Alaska,
    Arizona
}

fn value_in_cents(c: Coin) {
    match c {
        // ...
        Coin::Quarter(state) => {
            println!("This is a Quarter and it's value is 25. It comes from {:?}", state);
        }
    }
}

fn main() {
    
    value_in_cents(Coin::Penny);
    value_in_cents(Coin::Nickel);
    value_in_cents(Coin::Dime);
    value_in_cents(Coin::Quarter(State::Alaska));
    value_in_cents(Coin::Quarter(State::Arizona));

}

```

## Matching Option Enum

```rust
fn main() {
    let five = Some(5);
    let six = plus_one(five);
    let none = plus_one(None);

    println!("{:?} {:?} {:?}", five, six, none);

}

fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        None => None,
        Some(i) => Some(i+1),
    }
}
```

## The `_` placeholder

Currently in the match case - you have to match all of the possible values it can accept. If the requirement is not met, an error will be thrown.

To fix this, you can use the `_` placeholder:

```rust
fn plus_one(x: Option<i32>) -> Option<i32> {
    match x {
        Some(i) => Some(i+1),
        _ => None,
    }
}
```

## Control flow using If Let

```rust
fn main() {
    let some_u8 = Some(3);

    if let Some(3) = some_u8 {
        println!("Three")
    }

}
```

## 