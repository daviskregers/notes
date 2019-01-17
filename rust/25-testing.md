# Writing automated tests in Rust

Rust provides support for automated tests. 

When using cargo, you can use command

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

You can use following macros:
- `assert!` - assert!(true)
- `assert_eq!` - assert_eq!(4, 2 + 2)


You can define custom failure messages like so:

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

## Running tests

The `cargo test` compiles a binary that is configured to run all the tests in parallel. 

You can provide some configuration like not to run tests in parallel:

```
cargo test -- --test-threads=1
```

To see output of the program:

```
cargo test -- --nocapture
```

Running a subset of tests:

```
cargo test test_name
cargo test check_guess
```

You can run multiple tests by providing a common phrase in test names, for example `this_test_will_pass` and `this_test_will_fail`:

```
cargo test this
```

To ignore tests, you can add:

```
#[test]
#[ignore]
fn ignored_test() {
    assert!(true)
}
```

## Test organization

In rust, the tests are organized into unit tests and integration tests. Unit tests are small, used to test single units in isolation. Integrated tests uses library as any other external library would.

### Unit testing

We will put unit tests, we will put them in each file of the `src/` directory, in a separate module `tests`:

```rust
#[cfg(test)]
mod tests {
    use super::*;
    #[test]
    fn it_works() {
        assert_eq!(2+2, 4)
    }
}
```

The `#[cfg(test)]` part tells the compiler not to include this module in the built version.

### Integration tests

In rust integration tests we will save in `tests/` directory, call `use extern package` where the package is project name, use methods under the package. Then everything works the same.

```rust

extern crate package;

mod tests {
    
    #[test]
    fn larger_can_hold_smaller() {
        let larger = package::Rectangle{length: 8, width: 7};
        let smaller = package::Rectangle{ length: 5, width: 1};
        assert!(larger.can_hold(&smaller))
    }

    #[test]
    fn smaller_cannot_hold_larger() {
        let larger = package::Rectangle{length: 8, width: 7};
        let smaller = package::Rectangle{ length: 5, width: 1};
        assert!(!smaller.can_hold(&larger));
    }

    #[test]
    fn test_add_two() {
        assert_eq!(4, package::add_two(2));
    }

    #[test]
    fn greeting_contains_name() {
        let result = package::greeting("Rob");
        assert!(result.contains("Rob fail"), "Greeting dod not contain name, value was {}", result);
    }

    #[test]
    #[should_panic]
    fn check_guess() {
        package::Guess::new(0);
    }

    #[test]
    #[ignore]
    fn ignored_test() {
        assert!(true)
    }

}

```