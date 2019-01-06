# Cargo

Cargo is a Rust's build system and package manager. This tool is used to manage rust projects.

To create a new project using cargo:

```
cargo new projectname --bin or --lib
```

To compile the project:

```
cargo build
cargo check
cargo run
```

## Crates

A crate is a package of rust code [https://crates.io/](https://crates.io/) with a binary or library type.

The crates / dependencies can be added to the `Cargo.toml' file:

```
[dependencies]
rand = "0.5.0"
```

Now, when running `cargo build`, it will automatically download the dependency.

Crates can be updated using the `cargo update`.

to include the crate in the code you can use

```
extern crate rand;
use rand::Rng;

fn main() {

}
```