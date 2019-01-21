# Modules

A module is a collection of methods, it is defined by a keyword `mod`.

```rust

mod client {
    fn connect() {}
}

mod network {
    fn connect() {}

    mod server {
        fn connect() {}
    }

}

```

You can also move the modules into separate files:

```rust
mod client;
```

and client.rs:

```rust 
fn connect() {}
```

## Controlling visibility

When making a library, usually we make a set of methods that users can use to do something. When we compile them, there will be a warning, that our project does not call them.

To prevent this, we can use the visibility keyword `pub`, which will mark it as a public API.

```
pub fn connect() {}
```

## Referring names to different modules

Normally, when using modules we need to do something like this:

```rust

pub mod a {
    pub mod series {
        pub mod of {
            pub fn nested_module() {

            }
        }
    }
}

fn main() {
    a::series::of::nested_module();
}

```
We can fix this by using a `use` keyword.

```rust
use a::series::of::nested_module;
fn main() {
    nested_module();
}
```

We can also use the `use` keyword with enums:

```rust
enum TrafficLight{
    Red, Yellow, Green
}

use TrafficLight::{Red,Yellow}
fn main() {
    let red = Red;
    let yellow = Yellow;
    let green = TrafficLight::Green;
}

```