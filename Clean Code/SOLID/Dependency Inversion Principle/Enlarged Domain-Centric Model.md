---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

- [[Ports and Adapters architecture]]
- [[Port]]s are seams we introduce by [[extracting interfaces]]
- [[Adapter]]s are [[plugin]]s which come from the [[boundary of a system]]
- Strive to keep the [[graph]] as flat as you can

Who is responsible for keeping the control over the [[dependency instantiation]] and their
[[lifetime]]?

Answer: "[[Main partition]] as the infrastructural point".

- Conforms to [[Single Choice Principle]].
- Only the [[main partition]] knows about dependencies and their relationships.