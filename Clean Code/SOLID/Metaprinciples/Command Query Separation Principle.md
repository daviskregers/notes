---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

Every [[method]] should either be a [[command]] that performs an action, or a [[query]] that returns data to the caller, but not both.

In other words, asking a question should not change the answer.

There are two major types of functions:
- Functions which perform commands
- Functions which perform a query and return a result

---

If we have a function that logs you in and returns the result.
We cannot really say if the user was already logged in - etc.

```csharp
public bool LogOn(string username, string password) { }
if (LogOn("admin", "qwerty")) { }
```

We should implement this way:

```csharp
public void LogOn(string username, string password) { }
public bool IsLoggedOn(string username, string password) { }
```
