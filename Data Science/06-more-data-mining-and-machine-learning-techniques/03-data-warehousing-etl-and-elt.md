# Data warehousing overview: ETL and ELT

### What is Data Warehousing?

- A large, centralized database that contains information from many sources
- Often used for business analysis in large corporations or organizations
- Queried via SQL or tools (i.e. Tableau)
- Often entire departments are dedicated to maintaining a data warehouse
    - Data normalization is tricky - how dows all of this data relate to each other? What views do people need?
    - Maintaining the data feeds is a lot of work
    - Scaling is tricky


## ETL: Extract, Transform, Load

- ETL and ELT refer to how data gets into a data warehouse.
- Traditionally, the flow was Extract, Transform, Load:
    - Raw data from operational systems is first periodically extracted
    - Then the data is transformed into the schema needed by the data warehouse
    - Finally, the data is loaded into the data warehouse, already in the structure needed
- But what if we're dealing with "big data"? That transform step can turn into a big problem.

### ELT: Extract, Load, Transform

- Today, a huge oracle instance isn't the only choice for a large data warehouse
- Things like Hive let you host massive databases on a Hadoop cluster
- Or, you might store in a large, distributed NoSQL data store
    - and query it using things like Spark or MapReduce.
- The scalability of Hadoop let's you flip the loading process on it's head.
    - Extract raw data as before
    - Load it as is
    - Then use the power of hadoop to transform it in place.
