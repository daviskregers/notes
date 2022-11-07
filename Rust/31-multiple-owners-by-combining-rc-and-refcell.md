# Multiple Owners by combining Rc and RefCell

When using Rc we can have multiple owners of data, but only gives us immutable access to that data, by using the RefCell, we can gain mutable access to it.

```rust
use std::rc::Rc;
use std::cell::RefCell;

fn main() {
    
    let value = Rc::new(RefCell::new(5));
    let a = Rc::clone(&value);
    let b = Rc::clone(&value);

    *value.borrow_mut() += 5;
    println!("a {:?}", a);
    *value.borrow_mut() += 5;
    println!("b {:?}", b);
    *value.borrow_mut() += 5;
    println!("value {:?}", value)

}
```

The output:

```
davis@davis-arch  ~/projects/rust   master  ./31_rc_refcell 
a RefCell { value: 10 }
b RefCell { value: 15 }
value RefCell { value: 20 }
```
