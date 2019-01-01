# Installing rust

You can visit the [Install Rust](https://www.rust-lang.org/tools/install) site for instructions.

```bash
curl https://sh.rustup.rs -sSf | sh
```

```
✘ davis@davis-arch  ~  curl https://sh.rustup.rs -sSf | sh
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust programming 
language, and its package manager, Cargo.

It will add the cargo, rustc, rustup and other commands to Cargo's bin 
directory, located at:

  /home/davis/.cargo/bin

This path will then be added to your PATH environment variable by modifying the
profile files located at:

  /home/davis/.profile
  /home/davis/.zprofile
  /home/davis/.bash_profile

You can uninstall at any time with rustup self uninstall and these changes will
be reverted.

Current installation options:

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
  modify PATH variable: yes

1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

```
source $HOME/.cargo/env
```

To verify that everything is working, you can make a new `hello.rs` file with the following contents:

```rust
fn main() {
    println!("Hello World");
}
```

and compile it:

```bash
rustc hello.rs
```

Then, finally run it:

```bash
davis@davis-arch  ~/projects/rust  ./hello
Hello World
```

You can also use online resources to compile and run it online like [repl.it](https://repl.it) or [Rust playground](https://play.rust-lang.org).