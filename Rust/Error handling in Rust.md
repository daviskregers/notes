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


In [[Rust language]] there are two types of errors - [[Recoverable errors]] and [[Unrecoverable errors]].

```rust

use std::fs::File;
use std::io::ErrorKind;
use std::io::Read;

fn main() {
    
    let f = File::open("hello.txt");
    // Err(Os { code: 2, kind: NotFound, message: "No such file or directory" })
    println!("{:?}", f);

    let _f1 = match f {
        Ok(file) => file,
        Err(_error) => {
            panic!("File not found")
        }
    };

    // Match error types 

    let f = File::open("hello.txt");

    let _f2 = match f {
        Ok(file) => file,
        Err(ref error) if error.kind() == ErrorKind::NotFound => {
            match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => {
                    panic!("Not able to create file {:?}", e)
                }
            }
        },
        Err(error) => {
            panic!("Unable to Open File {:?}", error);
        }
    };

    // Unwrap

    let _f = File::open("abc.txt").unwrap(); // Calls panic! for us when file not found

    // Expect

    let _f = File::open("abc.txt").expect("failed"); // Returns failed

    // Propagating errors

    let output = read();
    match output {
        Ok(fi) => println!("{:?}", fi),
        Err(e) => println!("{:?}", e),
    }

    // Propagating using ?

    let output = read_q();
    match output {
        Ok(fi) => println!("{:?}", fi),
        Err(e) => println!("{:?}", e),
    }

    // Throws an unrecoverable error
    panic!("Checking how panic works");

    let a = [1,2,3];
    // Throws unrecoverable error - out of bounds
    a[99]; 

}

fn read() -> Result<String, std::io::Error> {
    let f = File::open("hello.txt");
    let mut f = match f {
        Ok(file) => file,
        Err(e) => return Err(e),
    };

    let mut s = String::new();
    match f.read_to_string(&mut s) {
        Ok(_) => Ok(s),
        Err(e) => Err(e),
    }
}

fn read_q() -> Result<String, std::io::Error> {
    let mut f = File::open("hello.txt")?;
    let mut s = String::new();
    f.read_to_string(&mut s)?;
    Ok(s)
}

```