---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/interface-segregation-principle, review]
Review: Hard
---

- [[Liskov Substitution Principle]] violation smell often indicates a violation of [[Interface Segregation Principle]]
- Client's code references a [[class]] but uses only a small portion of it's [[API]]
    - Fat [[interface]] -> segregate it
    - Fat [[interface]] which is not under your control -> [[Facade design pattern]]
- [[Adapter Design Pattern]]
    
## Tips

- General algorithm of "fixing" fat interfaces
    - Create narrower interface
    - Fat interface inherits from that narrow interface
    - Client uses the narrow interface
- Don't abuse ISP by creating tons of small interfaces
