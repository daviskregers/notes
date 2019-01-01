# Data types in rust

Rust is a statically typed language - the compiler must know the data type of each variable. The compiler can usually infer what type we want to use based on the value and how we use it.

We need to define type of variable in cases when many types are possible, such as when we are converting a String to a numberic type.

----

In rust there are 2 types of data types:
- Scalar - represents a single value (1, 9.4, 'c')
  -  Integer
<table>
    <tr>
        <th>Length</th>
        <th>Signed</th>
        <th>Unsigned</th>
    </tr>
    <tr>
        <td>8-bit</td>
        <td>`i8`</td>
        <td>`u8`</td>
    </tr>
    <tr>
        <td>16-bit</td>
        <td>`i16`</td>
        <td>`u16`</td>
    </tr>
    <tr>
        <td>32-bit</td>
        <td>`i32`</td>
        <td>`u32`</td>
    </tr>
    <tr>
        <td>64-bit</td>
        <td>`i64`</td>
        <td>`u64`</td>
    </tr>
    <tr>
        <td>128-bit</td>
        <td>`i128`</td>
        <td>`u128`</td>
    </tr>
    <tr>
        <td>arch</td>
        <td>`isize`</td>
        <td>`usize`</td>
    </tr>
</table>
  -  Floating-point number
  -  Boolean
  -  Character
     -  Enclosed with single quotes.
- Comound

```rust
ffn main() {
    let a:i128 = -1;
    let b:u8 = 1;
    let c:f32=132.0048;
    let d:bool = true;
    let e:char = 'c';
    println!(" {} {} {} {} {}", a, b, c, d, e);
}
```

```bash
davis@davis-arch  ~/projects/rust  ./datatypes       
 -1 1 132.0048 true c
```