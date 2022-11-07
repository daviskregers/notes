# How to refactor

It should be done as a series of small changes, where each makes the code slightly better while still leaving the program in working order.

## Checklist

- Code should become cleaner.
	- If the code hasn't become cleaner - try to figure out what happened.
	- Usually happens with a mix of small changes into one big change.
	- Can also happen with extremely sloppy code. In this case it's worthwhile to thing about completely rewriting parts of the code.
		- Before proceeding, it should be covered with tests.
- New functionality shouldn't be created during refactoring.
- All existing tests must pass after refactoring.
	- Cases when tests break down after refactoring.
		- You made an error, go fix it.
		- Tests are too low-level. 
			- e.g. you were testing private methods.
			- Refactor tests or write new set of higher-level tests.
			- Write BDD-style tests.
			
			
