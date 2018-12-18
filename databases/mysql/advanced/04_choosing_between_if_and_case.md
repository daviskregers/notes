# Choosing bethween IF and CASE statements

When deciding to use either `IF` or `CASE` statements, you should take following points into consideration:

- A simple `CASE` statement is much more readable than the `IF` statement when you compare a single expression against a range of unique values. In addition, the simple `CASE` statement is more efficient than the `IF` statement.
- When you check complex expressions based on multiple values, the `IF` statement is easier to understand.
- If you choose to use the `CASE` statement, you have to make sure that at least one of `CASE` conditions is matched. Otherwise, you need to define an error handler to catch the error. Recall that you do not have to do this in the `IF` statement.
