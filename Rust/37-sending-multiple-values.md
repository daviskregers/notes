# Sending multiple values

If we try to print the value sent in the previous section:

```rust
use std::sync::mpsc; // multiple producer, single consumer
use std::thread;

fn main() {
    let (sender, reciever) = mpsc::channel();
    thread::spawn(move || {
        let val = String::from("hi");
        sender.send(val).unwrap();
        println!("{}", val);
    });

    let rec = reciever.recv().unwrap();
    println!("Got {}", rec);

}
```

While compiling, we will get an error `use of moved value` because the value has been sent to another thread. 

we can use something like this:

```
use std::sync::mpsc; // multiple producer, single consumer
use std::thread;
use std::time::Duration;

fn main() {
    let (sender, reciever) = mpsc::channel();
    thread::spawn(move || {
        let vals = vec!["hi", "from", "the", "thread"];

        for val in vals {
            sender.send(val).unwrap();
            thread::sleep(Duration::from_secs(1))
        }

    });

    for received in reciever {
        println!("Got {}", received);
    }  

}
```

Output:

```
davis@davis-arch  ~/projects/rust   master  ./37-sending-multiple-values
Got hi
Got from
Got the
Got thread
```
