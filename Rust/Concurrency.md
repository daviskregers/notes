---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust, review]
sr-due: 2023-01-27
sr-interval: 58
sr-ease: 250
---

One of the rusts major goal is to handle [[concurency]] safely and efficiently, where parts of program  are executed at the same time. By [[ownership]] and [[type checking]], many [[concurency errors]] are thrown at the [[compile time]].

## Concurrency vs parallelism

In [[concurrency]], suppose we have one [[CPU core]] and three [[process]]es that are being ran at the same time. The CPU will switch between these processes using an [[algorithm]] like [[Round Robin]], saving the progress of it.

In [[Parallelism]], the CPU will have more than 1 core and it will be able to run more than 1 process at the same time while still using [[concurrency]] to switch between the processes.