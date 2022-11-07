# Using Join Handles

Looking at the last section, we can see that the main thread stops and the spawned thread does not finish it's work. We can use Join Handles to ensure that all threads finish their tasks before exiting.

```rust

use std::thread;
use std::time::Duration;

fn main() {

    let handle = thread::spawn(|| {
        for i in 1 .. 10 {
            println!("Hello from thread {}", i);
            thread::sleep(Duration::from_millis(1));
        }
    });

    for i in 1..10 {
        println!("Hello from main {}", i);
        thread::sleep(Duration::from_millis(1));
    }

    handle.join().unwrap();

}

```

Output:

```
davis@davis-arch  ~/projects/rust   master  ./34_join_handle 
Hello from main 1
Hello from thread 1
Hello from main 2
Hello from thread 2
Hello from main 3
Hello from thread 3
Hello from main 4
Hello from thread 4
Hello from main 5
Hello from thread 5
Hello from main 6
Hello from thread 6
Hello from main 7
Hello from thread 7
Hello from main 8
Hello from thread 8
Hello from main 9
Hello from thread 9
```