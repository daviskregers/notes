# Tuples and arrays in Rust

## Tuple

Tuple is a comound data type.  You can store a list of different data type elements in it.

Tuples have a fixed length: once declared, they cannot change it's length.

```rust
let tup: (i32, f64, u8) = (326, 4.9, 22)
```

When you assign a tuple to a variable - it is known as destructing.

Tuple indexes start at 0.

```rust
fn main() {
    let a: (i32, bool, f64) = (220, true, 8.5);
    print_tuple(a);
}

fn print_tuple(x :  (i32, bool, f64)) {
    let (a, y, z) = x;
    println!("{}, {}, {}", a, y, z);
}
```

### Arrays

Array is a collection of values, must be in the same type and the length is fixed.

```rust 
let a = [1,2,3,4,5];
let a: [i32;5] = [1,2,3,4,5];
let a: [i32;5] = [0;5] // Will return 5 zero values.
```

The values can be accessed just like in other programming languages using `variable[index]`.

```rust
fn main() {
    let a: [i32; 5] = [3;5];
    print_array(a);
}

fn print_array(x: [i32;5]) {
    for n in x.iter() {
        println! ("{}", n);
    }
}
```