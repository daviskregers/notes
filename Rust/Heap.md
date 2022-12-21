---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

### Heap

Heap can store data with a size unknown at [[compile time]] or a size that might change instead.

For example, in the [[String]] the [[push_str]] method.

The heap is less organised.

The [[Operating System]] finds an empty spot somewhere in the heap that is big enough, marks it as being in use.

When used, returns a [[pointer]], which addresses a location in memory.

This process is called [[allocating on the heap]].

---

Allocating a large amount of space on the heap can take time.

