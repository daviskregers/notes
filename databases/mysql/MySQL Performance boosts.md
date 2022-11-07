# Performance boosts

## InnoDB Buffer Pool Size

1. Holds the data and indexes of tables in memory.
2. Bigger buffer results in faster row lookups.
3. The bigger the better, default is 8MB.
4. Use InnoDB where it requires.

## Query Cache

1. Keeps the result of queries in memory until invalidated by writes.
2. `query_cache_size` - total size of memory available to query caching, the default is 128 MB.
3. `query_cache_limit` - the maximum number of kilobytes one query can take up in the cache, default is 8MB.


## Writing Queries

1. When writing bad queries, the performance will be bad no matter the scale.
2. Use `EXPLAIN` to profile the query execution plan
3. Use `DISTINCT` not `GROUP BY`
4. Never use an indexed column with a function
5. Avoid using functions in where clause

## SSD

Use a Solid State Drives (SSD) for database servers as they are better for latency and access time than regular HDDs.