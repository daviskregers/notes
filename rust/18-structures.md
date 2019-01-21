# Structures

A struct or structure is a custom data type that lets you to name and package together multiple related values.

Structs are similar to tuples, the pieces of a struct can be different types, but unlike the tuples - each piece of data is predefined so it's clear what each value means.

## Define struct

```rust
    struct User {
        username: String,
        email: String,
        age: i8
    }
```

## Instantiate struct

You can instantiate the structs using following:

```rust
let user = User {
        email: String::from("email@example.org"),
        username: String::from("example-username"),
        age: 21
    };
```

## Debug struct

In order to be able to use something like this:

```rust
println!("{:?}", user)
```

You will need to add the debug functionality for the struct:

```rust
#[derive(Debug)]
struct User {
    email: String,
    username: String,
    age: i8
}
```

## Access values

To get a specific value from a struct, we use dot notation like `user.email`.

In order to change values the instance needs to be mutable, making only certain fields mutable is not supported.

```rust
user.age = 23;
```

## Return instance from a function

Returning instance from a function

```rust

fn build_user(age: i32) -> User {
    User {
        age: age,
    }
}
```

If the fields variable name matches the attribute name, we can use shorthand syntax:

```rust

fn build_user(age: i32, name: String) -> User {
    User {
        age, name
    }
}
```

## Update Structs

Updating structs:

```rust
let u1 = User {
    email: String::from("email@example.org"),
    username: String::from("example-username"),
    age: 21
}

let user2 = User {
    email: String::from("email2@example.org"),
    ..user
};
println!("{:?}", &user2);

```

## Methods

Methods are similar to functions - they're declared with the fn keywords and their name, but they are declared in the context of a struct.

Their first parameter is always self, which represents the instance of the struct.

```rust

struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {

    fn area(&self) -> u32 {
        self.width * self.height
    }

    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }

}

```

## Associated function

When we define a function within `impl` block that does not take the `self` as a parameter, we call them associated functions.

They are still functions not methods, because they don't have an instance of a struct to work with.

These functions are often used for constructors that will return a new instance of a struct.

```rust

impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle { width: size, height: size }
    }
}

```


