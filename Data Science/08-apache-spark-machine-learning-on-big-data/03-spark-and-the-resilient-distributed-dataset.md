# Spark and the Resilient Distributed Dataset (RDD)

## The SparkContext

- Created by your dirver program
- Is responsible for making RDDs resilient and distributed
- Creates RDD's
- The spark shell creates a "sc" object for you

## Creating rdd's

- nums = parallelize([1,2,3,4])
- sc.testFile("file:///somewhere/test.txt")
    - or s3n://, hdfs://
- hiveCtx = HiveContext(sc) rows = hiveCtx.sql("SELECT name, age FROM users")
- Can also create from:
    - JDBC
    - Cassandra
    - HBase
    - Elasticsearch
    - JSON, CSV, sequence files, object files, various compressed formats

## Transforming RDD's

- Map
    - rdd = sc.parallelize([1,2,3,4])
    - rdd.map(lambda x: x*x)
    - this yields 1,4,9,16
- Flatmap
- Filter
- Distinct
- Sample
- Union, intersection, subtract, cartesian

## RDD Actions

- Collect
- Count
- CountByValue
- Take
- Top
- Reduce
- and more

## Lazy evaluation

- Nothing actually happens in your driver program until an action is called.
