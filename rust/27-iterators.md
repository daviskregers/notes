# Iterators

We can process a series of items with a iterator:

```rust
fn main() {
    
    let v1 = vec![1,2,3];
    let v1_iter=v1.iter();

    for val in v1_iter {
        println!("{}", val)
    }

}
```

We can also use 
```
let mut v1_iter2=v1.iter();
assert_eq!(v1_iter2.next(), Some(&1));
assert_eq!(v1_iter2.next(), Some(&2));
assert_eq!(v1_iter2.next(), Some(&3));
assert_eq!(v1_iter2.next(), None);
```

You can use iterators in following ways:

```rust
let v1:Vec<i32> = vec![1,2,3];
let v2:Vec<_> = v1.iter().map(|x| x + 1).collect();
assert_eq!(v2,vec![2,3,4]);
```

You can create your own iterator trait in a following manner:

```rust
struct Counter {
    count: u32
}
impl Counter {
    fn new() -> Counter {
        Counter{count: 0}
    }
}
impl Iterator for Counter {
    type Item = u32;
    fn next(&mut self) -> Option<Self::Item> {
        self.count += 1;
        if(self.count < 6) {
            Some(self.count)
        } else {
            None
        }
    }
}

let mut counter = Counter::new();
assert_eq!(counter.next(), Some(1));
assert_eq!(counter.next(), Some(2));
assert_eq!(counter.next(), Some(3));
assert_eq!(counter.next(), Some(4));
assert_eq!(counter.next(), Some(5));
assert_eq!(counter.next(), None);

fn using_other_iterator_trait_methods() {
    let sum:u32 = Counter::new().zip(Counter::new().skip(1)).map(|(a,b)| a*b).filter(|x| x%3 ==0).sum();
    assert_eq!(18, sum);
}

using_other_iterator_trait_methods();

```



