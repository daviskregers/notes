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

We can clone the sender to use more than one [[transmit]] of the [[channel]].

```rust
use std::thread;
use std::sync::mpsc;
use std::time::Duration;

fn main() {
    let (s, r) = mpsc::channel();
    let s1 = mpsc::Sender::clone(&s);

    thread::spawn( move || {
        let vals = vec!["hi", "from", "the", "thread"];

        for val in vals {
            s.send(val).unwrap();
            thread::sleep(Duration::from_secs(1))
        }

    });

    thread::spawn( move || {
        let vals = vec!["more", "messages", "for", "you"];

        for val in vals {
            s1.send(val).unwrap();
            thread::sleep(Duration::from_secs(1))
        }

    });

    for rec in r {
        println!("{}", rec);
    }

}
```

This will produce an output like this:

```
davis@davis-arch  ~/projects/rust   master  ./38-multiple-producers-by-cloning-transmitter
more
hi
messages
from
the
for
you
thread
```