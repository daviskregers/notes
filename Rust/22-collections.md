# Collections

Rust has a set of data structures called collections. Collections can have different data types and are stored in heap - data does not need to be known at compile time.

## Vectors

Vectors store a collection of the same type data. For example, if one element in vector is `i32`, every single element must be `i32`.

```rust
fn main() {
    let mut v = Vec::new();
    v.push(20);
    v.push(30);
    v.push(40);
    println!("{:?}", v);

    for i in &mut v {
        println!("{}", i);
        *i*=2;
        println!("{}", i);
    }

    let v:Vec<i32> = vec![1,2,3];
    println!("{:?}", v);

    let value = &v[0]; // will thow an error if the value does not exist
    println!("{:?}", value);

    let value = &v.get(0); // Will return None if value does not exist, Some if exist

    println!("{:?}", value);

}
```

### Storing multiple types in Vector

```rust

#[derive(Debug)]
enum SpreadSheet {
    Integer(i32),
    Float(f64),
    Text(String),
}

fn main() {
    let row = vec![
        Spreadsheet::Integer(3), 
        Spreadsheet::Float(3.14), 
        Spreadsheet::Text(String::from("Hello"))
    ];

    println!("{:?}", row);

}

```

## String collection

```rust
fn main() {
    
    // .to_string(), .push_str, .push()

    let a = 1;
    let mut s = a.to_string();
    s.push_str(" Hello");
    s.push('O');
    println!("{}", s);

    // + operator

    let s1 = String::from("Hello");
    let s2 = String::from("World");
    let s3 = s1 + &s2;
    println!("{}", s3);

    // format! macro

    let s1 = String::from("Hello");
    let s2 = String::from("World");
    let s3 = format!("{} {}", s1, s2);
    println!("{}", s3);

    // chars method 

    for n in "Hello".chars() {
        println!("{}", n)
    }


}
```

## HashMap

```rust

use std::collections::HashMap;

fn main() {

    let mut score = HashMap::new();
    score.insert("Blue", 10);
    score.insert("Red", 20);
    println!("{:?}", score);

    // collect

    let team = vec!["Blue", "Red"];
    let score = vec![10, 20];
    let scores:HashMap<_,_> = team.iter().zip(score.iter()).collect();
    println!("{:?}", scores);

    // get

    let mut scores = HashMap::new();
    scores.insert("Blue", 10);
    scores.insert("Yellow", 20);
    let score = scores.get("Yellow");
    println!("{:?}", score);

    // Iterate

    let mut scores = HashMap::new();
    scores.insert("Blue", 10);
    scores.insert("Yellow", 20);

    for (key, value) in &scores {
        println!("{} {}", key, value);
    }

    // Updating HashMap

    let mut score = HashMap::new();
    score.insert("Blue", 10);
    score.insert("Green", 15);
    score.entry("Blue").or_insert(20);
    score.entry("Red").or_insert(20);
    score.insert("Green", 25);
    println!("{:?}", score);

}

```