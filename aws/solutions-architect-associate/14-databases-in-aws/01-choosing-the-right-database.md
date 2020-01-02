# Choosing the right database

- We have a lot of managed databases on AWS to choose from
- Questions to choose the right database based on your architecture
    - Ready-heavy, write-heavy, or balanced workload? Throughput needs? Will it change, does it need to scale or fluctuate during the day?
    - How much data to store and for how long? Will it grow? Average object size? How are they acessed?
    - Data durability? Source of truth for the data?
    - Latency requirements? Concurrent users?
    - Data model? How will you query the data? Joins? Structured? Semi-Structured?
    - Strong schema? More flexibility? Reporting? Search? RBDMS / NoSQL?
    - License costs? Switch to Cloud Native DB such as Aurora?

## Database types

- RDBMS (= SQL/OLTP): RDS, Aurora - great for joins
- NoSQL database: DynamoDB (~JSON), ElastiCache (key/value pairs), Neptune (graphs) - no joins, no SQL
- Object Store: S3 (for big objects) / Glacier (for backups / archives)
- Data Warehouse (= SQL Analytics / BI): Redshift (OLAP), Athena
- Search: ElasticSearch (JSON) - free text, unstructured searches
- Graphs: Neptune - display relationships between data

