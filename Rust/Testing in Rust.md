---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust/testing, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

# Writing automated tests in Rust

Rust provides support for [[automated tests]]. 

When using [[cargo]], you can use command

```
cargo test
```

It will compile and run the tests.

You can add tests in the `.rs` files using following syntax:

```rust

struct Rectangle {
    length: u32,
    width: u32
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        return self.length > other.length && self.width > other.width;
    }
}

fn add_two(a:i32) -> i32 {
    return a + 2;
}

#[cfg(test)]
mod tests {
    use super::*;
    #[test]
    fn larger_can_hold_smaller() {
        let larger = Rectangle{length: 8, width: 7};
        let smaller = Rectangle{ length: 5, width: 1};
        assert!(larger.can_hold(&smaller))
    }

    #[test]
    fn smaller_cannot_hold_larger() {
        let larger = Rectangle{length: 8, width: 7};
        let smaller = Rectangle{ length: 5, width: 1};
        assert!(!smaller.can_hold(&larger));
    }

    #[test]
    fn test_add_two() {
        assert_eq!(4, add_two(2));
    }

}

```

Now, when running the `cargo test`:

```
 daviskregers@Daviss-MacBook-Pro  ~/Projects/learning-rust/25-tests   master  cargo test
    Finished dev [unoptimized + debuginfo] target(s) in 0.04s
     Running target/debug/deps/tests-394413f4ff767751

running 3 tests
test tests::larger_can_hold_smaller ... ok
test tests::test_add_two ... ok
test tests::smaller_cannot_hold_larger ... ok

test result: ok. 3 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out

   Doc-tests tests

running 0 tests

test result: ok. 0 passed; 0 failed; 0 ignored; 0 measured; 0 filtered out
```

You can use following [[macros]]:
- `assert!` - assert!(true)
- `assert_eq!` - assert_eq!(4, 2 + 2)


You can define [[custom failure messages]] like so:

```
assert!(result.contains("Rob"), "Greeting dod not contain name, value was {}");
```

The output will be:

```
---- tests::greeting_contains_name stdout ----
thread 'tests::greeting_contains_name' panicked at 'Greeting dod not contain name, value was Hello Rob!', src/lib.rs:46:9
note: Run with `RUST_BACKTRACE=1` for a backtrace.
```

You can also assert that the test will cause a panic using the `#[should_panic]` :

```rust

struct Guess {
    value: i32,
}

impl Guess {
    fn new(value: i32) -> Guess {
        if value < 1 || value > 100 {
            panic!("Guess must be between 1 to 100, got {}", value)
        }
        Guess {
            value
        }
    }
}

#[cfg(test)]
mod tests {
    use super::*;

    #[test]
    #[should_panic]
    fn check_guess() {
        Guess::new(0);
    }

}

```

```
test tests::check_guess ... ok
```

![[Running Rust Tests]]

![[Rust Test Organization]]
