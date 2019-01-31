# Refcell and interior mutability

Using interior mutability allows you to mutate data even though it is a reference to a immutable data. Normally this is not allowed by rust, but we can use data structures to bend the rules of rust. A practical use case for interior mutability is used for mock objects while testing. 

```rust

pub trait Messenger {
    fn send(&self, msg: &str);
}

pub struct LimitTracker <'a, T: 'a+Messenger> {
    messenger: &'a T,
    value: usize,
    max: usize
}

impl <'a, T> LimitTracker <'a, T>
where T: Messenger {
    
    pub fn new (messenger: &T, max: usize) -> LimitTracker<T> {
        LimitTracker {
            messenger,
            value: 0,
            max,
        }
    }

    pub fn set_value(&mut self, value: usize) {
        
        self.value = value;
        let percent_of_max = self.value as f64 / self.max as f64;

        if percent_of_max >= 0.75 && percent_of_max < 0.9 {
            self.messenger.send("Warning, you've used over 75%!")
        } else if percent_of_max > 0.9 {
            self.messenger.send("Warning, you've used over 90%!")
        } else if percent_of_max >= 1.0 {
            self.messenger.send("You have reached your quota!")
        }

    }

}

#[cfg(test)]
mod test {
    use super::*;

    struct MockMessenger {
        sent_messages:Vec<String>,
    }
    impl MockMessenger {
        fn new() -> MockMessenger {
            MockMessenger { sent_messages:vec![] }
        }
    }
    impl Messenger for MockMessenger {
        fn send(&self, message: &str) {
            self.sent_messages.push(String::from(message));
        }
    }

    #[test]
    fn it_sends_over_75_percent_message() {
        let mock_messanger = MockMessenger::new();
        let mut limit_tracker = LimitTracker::new(&mock_messanger, 100);
        limit_tracker.set_value(80);
        assert_eq!(mock_messanger.sent_messages.len(), 1);
    }

}

```

When trying to compile this, it will throw an error with a following message:

```
✘ davis@davis-arch  ~/projects/rust/30_interior_mutability   master  cargo test
   Compiling interior_mutability v0.1.0 (/home/davis/projects/rust/30_interior_mutability)
error[E0596]: cannot borrow `self.sent_messages` as mutable, as it is behind a `&` reference
  --> src/lib.rs:53:13                                                 
   |                                                                   
52 |         fn send(&self, message: &str) {                           
   |                 ----- help: consider changing this to be a mutable reference: `&mut self`
53 |             self.sent_messages.push(String::from(message));       
   |             ^^^^^^^^^^^^^^^^^^ `self` is a `&` reference, so the data it refers to cannot be borrowed as mutable
                                                                       
error: aborting due to previous error                                  
                                                                       
For more information about this error, try `rustc --explain E0596`.    
error: Could not compile `interior_mutability`.                        
warning: build failed, waiting for other jobs to finish...
error: build failed                                                 
```

We can modify it to use RefCell:

```rust

use std::cell::RefCell;

pub trait Messenger {
    fn send(&self, msg: &str);
}

pub struct LimitTracker <'a, T: 'a+Messenger> {
    messenger: &'a T,
    value: usize,
    max: usize
}

impl <'a, T> LimitTracker <'a, T>
where T: Messenger {
    
    pub fn new (messenger: &T, max: usize) -> LimitTracker<T> {
        LimitTracker {
            messenger,
            value: 0,
            max,
        }
    }

    pub fn set_value(&mut self, value: usize) {
        
        self.value = value;
        let percent_of_max = self.value as f64 / self.max as f64;

        if percent_of_max >= 0.75 && percent_of_max < 0.9 {
            self.messenger.send("Warning, you've used over 75%!")
        } else if percent_of_max > 0.9 {
            self.messenger.send("Warning, you've used over 90%!")
        } else if percent_of_max >= 1.0 {
            self.messenger.send("You have reached your quota!")
        }

    }

}

#[cfg(test)]
mod test {
    use super::*;

    struct MockMessenger {
        sent_messages:RefCell<Vec<String>>,
    }
    impl MockMessenger {
        fn new() -> MockMessenger {
            MockMessenger { sent_messages:RefCell::new(vec![]) }
        }
    }
    impl Messenger for MockMessenger {
        fn send(&self, message: &str) {
            self.sent_messages.borrow_mut().push(String::from(message));
        }
    }

    #[test]
    fn it_sends_over_75_percent_message() {
        let mock_messanger = MockMessenger::new();
        let mut limit_tracker = LimitTracker::new(&mock_messanger, 100);
        limit_tracker.set_value(80);
        assert_eq!(mock_messanger.sent_messages.borrow().len(), 1);
    }

}

```

Now the test will pass:

```
✘ davis@davis-arch  ~/projects/rust/30_interior_mutability   master  cargo test
   Compiling interior_mutability v0.1.0 (/home/davis/projects/rust/30_interior_mutability)
warning: unused import: `std::cell::RefCell`                           
 --> src/lib.rs:1:5                                                    
  |                                                                    
1 | use std::cell::RefCell;                                            
  |     ^^^^^^^^^^^^^^^^^^                                             
  |                                                                    
  = note: #[warn(unused_imports)] on by default                        
                                                                       
    Finished dev [unoptimized + debuginfo] target(s) in 0.39s          
     Running target/debug/deps/interior_mutability-c8d57b4e53a0b271

running 1 test
test test::it_sends_over_75_percent_message ... ok

test result: ok. 1 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out

   Doc-tests interior_mutability

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

## RefCell borrow checker

```rust

let mut one_borrow=self.sent_messages.borrow_mut();
let mut two_borrow=self.sent_messages.borrow_mut();

one_borrow.push(String::from(message));
two_borrow.push(String::from(message));

```

This will throw `Already borrowed: BorrowMutError`.