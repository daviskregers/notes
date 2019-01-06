# Generic types, traits, lifetimes

In every language there are tools for handling duplicate concepts.

In Rust one such type is generics.

## Removing duplication

Removing a duplication by extracting a function:

```rust

fn main() {
    let list = vec![23,54,65,67]
    let mut largest = list[0];
    for n in list {
        if n > largest {
            largest = n;
        }
    }
    println!("Largest No. {}", largest);

    let list = vec![223,544,655,67]
    let mut largest = list[0];
    for n in list {
        if n > largest {
            largest = n;
        }
    }
    println!("Largest No. {}", largest);

}

```

```rust

fn main() {
    
    let list = vec![23,54,65,67];
    let result = largest(&list);
    println!("{}", result);

    let list = vec![223,544,655,67]
    let result = largest(&list);
    println!("{}", result);

    let list = vec!['y','t','u']
    let result = largest_char(&list);
    println!("{}", result);

}

fn largest(list :&[i32]) -> i32 {
    let mut largest = list[0];
    for n in list {
        if n > largest {
            largest = n;
        }
    }
    largest
}

fn largest_char(list :&[char]) -> char {
    let mut largest = list[0];
    for n in list {
        if n > largest {
            largest = n;
        }
    }
    largest
}

```

Now remove the duplication of the functions with different types:


```rust

fn main() {
    
    let list = vec![23,54,65,67];
    let result = largest(&list);
    println!("{}", result);

    let list = vec![223,544,655,67];
    let result = largest(&list);
    println!("{}", result);

    let list = vec!['y','t','u'];
    let result = largest_char(&list);
    println!("{}", result);

}

fn largest<T:PartialOrd+Copy>(list :&[T]) -> T {
    let mut largest = list[0];
    for n in list {
        if n > &largest {
            largest = *n;
        }
    }
    largest
}

```

## Generics in structure definition

``` rust 

#[derive(Debug)]
struct Point<T> {
    x: T,
    y: T,
}

fn main() {
    let integer = Point{x:5, y:10};
    let float = Point{x:8.0, y:9.4};
    println!("{:?}\n{:?}", integer, float);
}

```

## Generics in Enum definition

``` rust 

enum Option<T> {
    Some(T),
    None,
}

enum Result<T, E> {
    Ok(T),
    Err(E)
}

#[derive(Debug)]
struct Point<T, E> {
    x: T,
    y: T,
}

impl <T> Point<T> {
    fn x(&self) -> &T {
        &self.x;
    }
}

```

## Concrete types in Generics

```rust

impl Point<f32> {
    fn number(&self) -> f32 {
        self.x
    }
}
impl Point<i32> {
    fn number(&self) -> i32 {
        self.x
    }
}

fn main() {
    let n = Point{x:2.2, y: 3.14};
    println!("{}", n.number());
    let n = Point{x:2, y: 3};
    println!("{}", n.number());
}

```

## Performance of code using generics

While using generics, there is no performance impact because Rust transforms these types at the compile time. 

## Defining traits

```rust

trait Summary {
    fn summarize(&self) -> String;
}

struct NewsArticle {
    headline: String,
    location: String,
    author: String,
    content: String,
}

impl Summary for NewsArticle {
    fn summarize(&self) -> String {
        format!("{}, by {} ({}) \n {}", self.headline, self.author, self.location, self.content)
    }
}

fn main() {

let news = NewsArticle {
        headline: String::from("The title"),
        location: String::from("The location"),
        author: String::from("The author"),
        content:String::from("The content"),
    };

    println!("News Article \n{}", news.summarize());

}

```

## Default implementation

You can define a default implementation of a trait method, if defined in the struct, it will be overwritten.

```rust
trait Summary {
    fn summarize(&self) -> String {
        String::from("Default implementation");
    }
}
```

## Lifetime Annotation syntax

```rust
fn main() {
    let s1 = "Hello";
    let s2 = "Bye";
    let result = longest(s1, s2);
    println!("{}", result);
}

fn longest(x: &str, y: &str) -> &str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

Will throw an error - "This function's return type contain a borrowed value, but the signature does not say wether it is borrowed from 'x' or 'y'."

```rust

fn main() {
    let s1 = "Hello";
    let s2 = "Bye";
    let result = longest(s1, s2);
    println!("{}", result);
}

fn longest<'a>(x: &'a str, y:&'a str) -> 'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

```

```rust
struct<'a> {
    name: &'a String,
}
impl <'a> S <'a> {
    fn fun(&self) -> &String {
        self.name
    }
}

fn main() {
    let s = S{
        name: &String::from("Name"),
    }
    println!("{}", s.fun());
}
```