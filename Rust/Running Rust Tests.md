---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust/testing, review]
sr-due: 2023-11-28
sr-interval: 363
sr-ease: 250
---

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
