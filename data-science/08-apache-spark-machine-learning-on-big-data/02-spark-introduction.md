# Spark introduction

- Spark is a fast an general engine for large-scale data processing.
- It's scalable, consists of:
    - Driver Program (spark context)
    - Cluster manager (spark, yarn)
    - Executors (cache, tasks)
- It's fast
    - Run programs up to 100x faster than hadoop mapreduce in memory, or 10x faster on disk
    - DAG Engine (directed acyclic graph) optimizes workflows
- It's hot
    - Amazon
    - Ebay: log analysis and aggregation
    - NASA JPL: Deep Space Network
    - Groupon
    - TripAdviser
    - Yahoo
    - Many others
- it's not hard
    - Code in python, java or scala
    - Built around one main concept - the resilient distributed dataset (RDD)
- Components:
    - Spark streaming
    - Spark SQL
    - MLLib
    - GraphX
    - Spark Core
- Python vs scala
    - Why python?
        - No need to compile, manage dependencies etc
        - Less coding overhead
        - You already know python
        - Lets us focus on the concepts instead of a new language
    - But...
        - Scala is probably more popular choice with spark
        - Spark is built in scala so coding scala is native to spark
        - New features, libraries tend to be scala first.
