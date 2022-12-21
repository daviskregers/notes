---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

# Passing channel to function

We can pass [[channel]]s to [[function]]s like this:

```rust
use std::thread;
use std::sync::mpsc;

fn main() {
    
    let (s,r) = mpsc::channel();
    let handle = thread::spawn(|| {
        run(s);
        run1(r);
    });
    handle.join().unwrap();
}

fn run (s: mpsc::Sender<i32>) {
    s.send(2).unwrap();
    s.send(3).unwrap();
}

fn run1(r : mpsc::Receiver<i32>) {
    let rc = r.recv().unwrap();
    println!("{}", rc);
    println!("{}", r.recv().unwrap());
}
```

Output:

```
davis@davis-arch  ~/projects/rust   master  ./39-passing-channels-to-functions
2
3
```