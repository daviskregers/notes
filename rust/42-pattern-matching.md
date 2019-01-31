# Pattern matching

Rust also supports pattern matching. 

## Match

```rust
   match is_tuesday {
        true => println!("Using purple as background color"),
        false => println!("Using orange as background color"),
        _ => println!("Using black as background color")
    };

    match x {
        1|2 => println!("hey!"),
        3...5 => println!("hey?"),
        _ => println!("bye ... ")
    }

```

## If let

```rust
if let Some(color) = favorite_color {
        println!("Using your favorite color {}", favorite_color)
    } else if is_tuesday {
        println!("Tuesday is green day");
    } else if let Ok(age) = age {
        if age > 30 {
            println!("Using purple as background color");
        } else {
            println!("Using orange as background color");
        }
    } else {
        println!("Using blue as background color");
    }
```

## While let and for let patterns

```rust

 let mut stack = Vec::new();
stack.push(1);
stack.push(2);
stack.push(3);

while let Some(top) = stack.pop() {
    println!("{}", top);
}

```

The loop stops, when the pop returns `None`.

## For let

```rust
let v = vec!["a", "b", "c"];
for (index, value) in v.iter().enumerate() {
    println!("{} is at index {}", value, index)
}
```

## Assignment

```rust
let (x, y, z) = (1,2,3);
println("{} {} {}", x,y,z);
```

## Refutable and irrefutable patterns

Patterns that will match for any value are called Refutable, patterns that can fail for some values are called Irrefutable. 

## Ref and Ref mut

```rust
let name = Some(String::from("Bob"))    ;

match name {
    Some(ref name) => println!("Found name {}", name),
    None => (),
}

println!("{:?}", name);
```


Output:

````
davis@davis-arch  ~/projects/rust   master  ./42-pattern-matching
Using orange as background color
Using purple as background color
3
2
1
a is at index 0
b is at index 1
c is at index 2
1 2 3
hey!
Some("John")
```
