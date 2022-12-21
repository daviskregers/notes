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