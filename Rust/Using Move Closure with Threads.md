---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust/testing, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

# Using Move Closure with Threads

We can use [[Move Closure]] to move data from one to another [[thread]].

```rust
use std::thread;
fn main() {
    let v = vec![1,2,3];
    let handle =  thread::spawn(||{
        println!("{:?}", v)
    });
    handle.join().unwrap();
}
```

This will throw a [[compile error]] `closure may outlive the current function, but it borrows v, which is owned by current function.` This means, that the thread may live as long as when the reference to v is no longer valid. 

By using `move` keyword, we can force the [[closure]] to move the [[ownership]] of the values:

```rust
use std::thread;
fn main() {
    
    let v = vec![1,2,3];
    let handle =  thread::spawn(move || {
        println!("{:?}", v)
    });

    handle.join().unwrap();
}
```

```
✘ davis@davis-arch  ~/projects/rust   master  ./35-move-closure-with-threads
[1, 2, 3]
```