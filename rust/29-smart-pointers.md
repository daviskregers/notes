# Smart pointers

A smart pointer is a variable that holds an address to a memory. The most common type of a pointer is the reference.

Smart pointers are data structures that act like references but they posses additional meta data. 

They own data and allow to modify them.

## Box

Box points to data on a heap and points to it. You can use it when you have data of a known type but an unknown size at the build time. Then, it is used in a situation where this size is needed to be known.

```
let b = Box::new(5);
println!("{}", b);
```

When the box runs out of scope, the memory is deallocated since the box itself is allocated in stack, the data in heap.

It can be used also in cases when otherwise it would throw errors about recursion:

```rust
use List::{Cons, Nil};

enum List {
    Cons(i32, Box<List>),
    Nil
}

fn main() {
    let list = Box::new(Cons(1, Box::new(Cons(2, Box::new(Cons(3, Box::new(Nil)))))));
}
```

## Dereference

Using deference, you can use smart pointers like references. It is used with `*` operator:

```rust
let x = 5;
let y = &x;
assert_eq!(5, x);
assert_eq!(5, *y);
```

## Deref trait

You can implement deref trait in a following manner:

```rust
use std::ops::Deref; 


struct MyBox<T>(T);

impl <T> MyBox<T> {
    fn new(x: T) -> MyBox<T> {
        MyBox(x)
    }
}

impl <T> Deref for MyBox<T> {
    type Target = T;
    fn deref(&self)->&T {
        &self.0
    }
}

let x = 5;
let y = MyBox::new(5);
assert_eq!(5,x);
assert_eq!(5, *y); // *(y.deref())
```

## Deref coercion

```rust

fn hello(name : &str) {
    println!("Hello, {}", name)
}

let m = MyBox::new(String::from("Rust"));
hello(&m);

```

## Drop Trait

Customize on how data is released when it is about to go out of scope.

```rust

struct CustomSmartPointer {
    data: String,
}
impl Drop for CustomSmartPointer {
    fn drop(&mut self) {
        println!("Dropping Custom smart pointer with data {}", self.data);
    }
}

let c = CustomSmartPointer{data:String::from("my stuff")};
let d = CustomSmartPointer{data:String::from("other stuff")};

println!("Custom smart pointer created")

```

Output:
```
Custom smart pointer created
Dropping Custom smart pointer with data other stuff
Dropping Custom smart pointer with data my stuff
```

Note that rust drops data in reverse order - the "other stuff" drops first.

You can drop value early by using:

```rust
let c = CustomSmartPointer{data:String::from("my stuff")};
drop(c)
```

## Reference count

There are situations when data has multiple owners:

```rust
use List::{Cons, Nil};
enum List {
    Cons(i32, Box<List>),
    Nil
}

let a = Cons(5, Box::new(Cons(10, Box::new(Nil))));
let b = Cons(3, Box::new(Cons(a)));
let c = Cons(4, Box::new(a));
```

This will throw an error about that the value has been moved.

To fix this, we can use a Rc:

```rust
use std::rc::Rc;

enum List {
    Cons(i32, Rc<List>),
    Nil
}

let a = Rc::new(Cons(5, Rc::new(Cons(10, Rc::new(Nil)))));
println!("Counter after creating a {}", Rc::strong_count(&a));
let b = Cons(3, Rc::clone(&a));
println!("Counter after creating a {}", Rc::strong_count(&a));
let c = Cons(4, Rc::clone(&a));
println!("Counter after creating a {}", Rc::strong_count(&a));
```

