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

We can use [[thread]]s to run parts of program at the same time to ensure that the program does it's tasks quicker. But now, it cannot ensure the order of the tasks that will be ran.

```rust
use std::thread;
use std::time::Duration;

fn main() {

    thread::spawn(|| {
        for i in 1 .. 10 {
            println!("Hello from thread {}", i);
            thread::sleep(Duration::from_millis(1));
        }
    });

    for i in 1..5 {
        println!("Hello from main {}", i);
        thread::sleep(Duration::from_millis(1));
    }

}
```

The output:

```
davis@davis-arch  ~/projects/rust   master  ./33_threads       
Hello from main 1
Hello from thread 1
Hello from main 2
Hello from thread 2
Hello from main 3
Hello from thread 3
Hello from main 4
Hello from thread 4

```

You can notice the [[thread]] only continues to iteration 4, that is because the [[main thread]] stops.

