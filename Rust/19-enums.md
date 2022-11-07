# Enums

## Enum

Enum allows you to define a type by enumerating it's possible values. 

For example, we work with IP addresses with 2 versions - IPv4 and IPv6. 

```rust

enum IpAddrKind {
    V4,
    V6
}

let four = IpAddrKind::V4;
let six = IpAddrKind::V6;

```

The reason this is useful is that both of these variants are now of the same type `IpAddrKind` and we can define a function that takes any `IpAddrKind`.

```rust
fn route(ip_type: IpAddrKind) {}
```

## Enum values

- Using enum as a type for fields of the structure.

let home = IPAddr {
    kind: IPAddrKind::V4,
    address: String::from("127.0.0.1)
}

let loopback = IPAddr {
    kind: IPAddrKind::V6,
    address: String::from("::1)
}

- Predefined values

```rust
enum Fruits {
    Apple = 0,
    Mango = 10,
    Watermelon = 20,
}

fn main() {
    let f = Fruits::Mango;
    println!("{:?}", f as i32);
}
```

- Using different types inside enum

```
enum IPAddr {
    V4(u8,u8,u8,u8),
    V6(String)
}

let home = IPAddr::V4(String::from(127,0,0,1));
let loopback = IPAddr::V6(String::from("::1"));

```

## Option Enum

Option, which is another enum defined by standard library.
The option type is used in many places because it encodes
the very common scenario in which a value could be something or could be nothing.

This functionality can prevent bugs that are extremely common in other programming languages.

Rust does not have `Null` types, but it does have an enum that
can encode the concept of a value being present or absent.

This enum is `Option<T>` and is defined by the standard library as follows:

```rust
enum Option<T> {
    Some(T),
    None
}
```