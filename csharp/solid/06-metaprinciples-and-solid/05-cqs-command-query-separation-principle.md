# CQS - Command Query Separation Principle

Every method should either be a command that performs an action, or a query that returns data to the caller, but not both.

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
