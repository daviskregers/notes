# Volatile and Stable dependencies

- What dependencies should we abstract away?
    - Volatile dependencies
        - Dependency itself depends on the environment (web servers, db)
        - Dependency doesn't yet exist and is still under development
        - Dependency which is not installed on all machines of developers
        - Dependencies has a nondeterministic behavior (randomizers inside)
        - If none of these are true, a dependency is stable.
        - Volatile dependencies are those which we want to abstract away by introducing levels of indirection.
