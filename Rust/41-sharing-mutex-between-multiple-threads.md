# Sharing Mutex between multiple threads

We can use mutex to modify data in multiple threads by using Arc:

```rust
use std::sync::{Mutex, Arc};
use std::thread;

fn main() {
    let counter = Arc::new(Mutex::new(0));
    let mut handles = vec![];

    for _ in 0 .. 10 {
        
        let counter = Arc::clone(&counter);

        let handle = thread::spawn( move || {
            let mut num = counter.lock().unwrap();
            *num += 1;
        });

        handles.push(handle);

    }

    for handle in handles {
        handle.join().unwrap();
    }

    println!("{}", *counter.lock().unwrap());

}
```

```
davis@davis-arch  ~/projects/rust   master  ./41-sharing-mutex-between-multiple-threads
10
```