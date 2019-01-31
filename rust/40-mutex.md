# Mutex

When using channels, the ownership of the data is being passed from one thread to another. We can use shared memory concurrency so we can access the data from multiple threads. We can use a Mutex for that.

The rules of mutex:
1. You must obtain the lock of the mutex before accessing it's data
2. When you are done with the data, you must release the lock

```rust
use std::sync::Mutex;

fn main() {
    
    let m = Mutex::new(5);
    
        {
            let mut num = m.lock().unwrap();
            *num = 6;
        }

    println!("m {:?}", m);

}
```

Output:

```
davis@davis-arch  ~/projects/rust   master  ./40-mutex 
m Mutex { data: 6 }
```
