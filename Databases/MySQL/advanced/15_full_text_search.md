# MySQL Full-Text Search

MySQL supports text searching by using the LIKE operator and regular expression. However, when the text column is large and the number of rows in a table is increased, using these methods has some limitations:

- Performance: MySQL has to scan the whole table to find the exact text based on a pattern in the `LIKE` statement or pattern in the regular expressions.
- Flexible search: with the `LIKE` operator and regular expression searches, it is difficult to have a flexible search query e.g., to find product whose description contains car but not classic.
- Revelance ranking: there is not way to specify which row in the result set is more relevant to the search terms.

Because ofthese limitations, MySQL extended a very nice feature so-called full-text search. Technically, MySQL creates an index from the words of the enabled full-text search columns and performs searches on this index. MySQL uses a sophisticated algorithm to determine the rows matched against the search query.

The following are important features of MySQL full-text search:

- Native SQL-like interface: you use the SQL-like statement to use the the full-text search.
- Fully dynamic index: MySQL automaticall updates the index of  text column whenever the data of that column changes.
- Moderate index size: it doesn't take much meemory to store the index
- Last but not least, it is fast to search based on complex search queries.

Notice that not all storage engines support the full-text search feature. In MySQL version 5.6 or later, only MyISAM and InnoDB storage engines support full-text search.

## Defining FULLTEXT Indexes for MySQL Full-Text Searching

Before performing a full-text search in a column of a table, you must index its data. MySQL will recreate the full-text index whenever the data of the column changes. In MySQL, the full-text index is a kind of index that has a name `FULLTEXT`.

MySQL supports indexing and re-indexing data automatically for a full-text search enabled column. MySQL version 5.6 or later allows you to defined afull-text index for a column whose data type is `CHAR`, `VARCHAR` or `TEXT` in MyISAM or InnoDB table type. Notice that MySQL supported full-text index in the InnoDB tables since 5.6

MySQL allows you to define the `FULLTEXT ` index by using the `CREATE TABLE` statement when you create the table or `ALTER TABLE` or `CREATE INDEX` statement for the existing tables.

```sql
CREATE TABLE table_name(
 column1 data_type, 
        column2 data_type,
        column3 data_type,
 …
PRIMARY_KEY(key_column),
FULLTEXT (column1,column2,..)
);
```

```sql
CREATE TABLE posts (
  id int(4) NOT NULL AUTO_INCREMENT,
  title varchar(255) NOT NULL,
  post_content text,
  PRIMARY KEY (id),
  FULLTEXT KEY post_content (post_content)
);
```

```sql
ALTER TABLE table_name  
ADD FULLTEXT(column_name1, column_name2,…)
```

```sql
ALTER TABLE products  
ADD FULLTEXT(productDescription,productLine)
```

```sql
CREATE FULLTEXT INDEX index_name
ON table_name(idx_column_name,...)
```

```sql
CREATE FULLTEXT INDEX address
ON offices(addressLine1,addressLine2)
```

```sql
ALTER TABLE offices
DROP INDEX address;
```

## Natural Language Full-Text searches

In natural language full-text searches, MySQL looks for rows or documents that are relevant to the free-text natural human language query, for example, "How to use MySQL natural language full-text searches".

Relevance is a positive floating-point number. When the relevance is zero, it means that there is no similarity. MySQL computes the relevance based on various factors including the number of words in the document, the number of unique words in the document, the total number of words in the collection, and the number of documents (rows) that contain a particular word.

To perform natural language full-text ssearches, you use `MATCH()` and `AGAINST()` functions. The `MATCH()` function specifies the column where you want to search and the `AGAINST()` function determines the expression to be used.

```sql
ALTER TABLE products 
ADD FULLTEXT(productline);

SELECT productName, productline
FROM products
WHERE MATCH(productline) AGAINST('Classic');
```

To search for product whose product line contains `Classic` or `Vintage` term, you can perform the following query.

```sql

SELECT productName, productline
FROM products
WHERE MATCH(productline) AGAINST('Classic,Vintage');
```

The `AGAINST()` function uses `IN NATURAL LANGUAGE MODE` search modifier by default therefore you can omit it in the query. There are other search modifieds e.g. `IN BOOLEAN MODE` for boolean text searches.

```sql
SELECT productName, productline
FROM products
WHERE MATCH(productline) 
AGAINST('Classic,Vintage' IN NATURAL LANGUAGE MODE)
```

By default, MySQL performs searches in the case-insensitive fashion. However, you can instruct MySQL to perform case-sensitive searches using binary collation for indexed columns.

### Sort the result set by relevance

A very important feature of full-text search is how MySQL ranks the rows in the result set based on their relevance. When the `MATCH()` funciton is used in the `WHERE` clause, MySQL returns the rows that are more relevant first.

The following example shows you how MySQL sorts the results set by relaveance.

```sql
SELECT productName, productline
FROM products
WHERE MATCH(productName) AGAINST('1932,Ford')
```

The products whose namaes contain both `1932` and `Ford` are returned first and the n the products whose names contains only the `Ford` keyword.

There are some important points you should remember when using the full-text search:

- The minimum length of the search term defined in MySQL full-text search engine is 4. It means that if you search for the keyword whose length is less than 4 e.g. car, car etc. you will not get any results.
- Stop words are ignored. MySQL defines a list of stop words in the MySQL source code distibution `storage/myisam/ft_static.c`

## Boolean Full-text searches

Besides the natural language full-text search, MySQL supports an additional form of full-text search that is called Boolean full-text search. In the Boolean mode, MySQL searches for words instead of the concept like in the natural language search.

MySQL allows you to perform a full-text search based on very complex queries in the Boolean mode along with Boolean operators. This is why the full-text search in Boolean mode is suitable for experienced users.

To perform a full-text search in the Boolean mode, you use the `IN BOOLEAN MODE` modifier in the `AGAINST` expression. The following example shows you how to search a product whose product name contains the `Truck` word.

```sql
SELECT productName, productline
FROM products
WHERE MATCH(productName) 
      AGAINST('Truck' IN BOOLEAN MODE )
```

To find the product whose product names contain the `Truck` word but not any rows that contain `Pickup`, you can use the exclude Boolean operator (`-`), which returns the result that excludes the `Pickup` keyword as the following query:

```sql
SELECT productName, productline
FROM products
WHERE MATCH(productName) AGAINST('Truck -Pickup' IN BOOLEAN MODE )
```

### MySQL Boolean full-text search operators

The following table illustrates the full-text seach Boolean operators and their meanings:

<table><thead><tr><th>Operator</th><th>Description</th></tr></thead><tbody><tr><td>+</td><td>Include, the word must be present.</td></tr><tr><td>–</td><td>Exclude, the word must not be present.</td></tr><tr><td>&gt;</td><td>Include, and increase ranking value.</td></tr><tr><td>&lt;</td><td>Include, and decrease the ranking value.</td></tr><tr><td>()</td><td>Group words into subexpressions (allowing them to be included, excluded, ranked, and so forth as a group).</td></tr><tr><td>~</td><td>Negate a word’s ranking value.</td></tr><tr><td>*</td><td>Wildcard at the end of the word.</td></tr><tr><td>“”</td><td>Defines a phrase (as opposed to a list of individual words, the entire phrase is matched for inclusion or exclusion).</td></tr></tbody></table>

The following examples illustrate how to use boolean full-text operators in search query

- `mysql tutorial` - to search for rows that contain at least one of the two words
- `+mysql +tutorial` - to search for rows that contain both words
- `+mysql tutorial` - to search for rows that contain the word `mysql`, but put the higher rank for the rank for the rows that contain tutorial.
- `+mysql -tutorial` - To search for rows that contain the word "mysql" but not "tutorial"
- `+mysql ~tutorial` - to search rows that contain word "mysql" and rank the row lower if it contains "tutorial".
`+mysql +(>tutorial <training>)` - To search for rows that contain the words "mysql" and "tutorial", or "mysql" and "training" in whatever order, but put the rows that contain "mysql tutorial" higher than "mysql training".
`my*` - To find rows that contain words starting with "my" such as mysql ...

### MySQL boolean full-text search main features

- MySQL does not automatically sort rows in the order of decreasing relevance in Boolean full-text search.
- To perform Boolean queries, InnoDBtables require all columns of the `MATCH` expression has a `FULLTEXT` index. Notice that MyISAM tables do not require this, although the search is quite slow.
- MySQL does not support multiple Boolean operators on a search query on InnoDB tables e.g., `++mysql`. MySQL will return an error if you do so. However, MyISAM behaves differently. It ignores other operators and uses the operator that is closest to the search word, for example, `+-mysql` will become `-mysql`.
- InnoDB full-text search does not support trailing plus (+) or minus (-) sign.It only supports leading plus or munis sign. MySQL will report an error if you search word is `mysql+` or `mysql-`. In addition, the following leading plus or minus with wildcard are invalid: `+*`, `+-`
- The 50% threshold is not applied. By the way, 50% threshold means if a word appears in more than 50% of the rows, MySQL will ignore it in the search result.

## MySQL Query expansion

In some cases, users want to search for information based on the knowledge that they have. Users use their experience to define keywords to search for information, and typically those keywords are too short.

To help users to find information based on the too-short keywords, MySQL full-text search engine introduces a concept called query expansion. 

The query expansion is used to widen the search result of the full-text searches based on `automatic relevance feedback` (or blin query expansion). Technically, MySQL full-text search engine performs the following steps when the query expansion is used:

1. MySQL full-text search engine looks for all rows that match the search query
2. It checks all rows in the search result and finds the relevant words
3. It performs a search again based on the relevant words instead of the original keywords provided by the users

From the application perspective, you can use the query expansion when the search results are too few. You perform the searches again but with query expansion to offer users more information that is related and relevant to what they are looking for.

To use the query expansion, you use the `WITH QUERY EXPANSION` search modifier in the `AGAINST()` function the following ilustrates the syntax of the query using the `WITH QUERY EXPANSION` search modifier.

```sql
SELECT column1, column2
FROM table1
WHERE MATCH(column1,column2) 
      AGAINST('keyword',WITH QUERY EXPANSION);
```

```sql
SELECT productName
FROM products
WHERE MATCH(productName) AGAINST('1992');

+-----------------------------------+
| productName                       |
+-----------------------------------+
| 1992 Ferrari 360 Spider red       |
| 1992 Porsche Cayenne Turbo Silver |
+-----------------------------------+
2 rows in set (0.00 sec)
```

```sql
SELECT productName
FROM products
WHERE MATCH(productName) 
      AGAINST('1992' WITH QUERY EXPANSION);

+-------------------------------------+
| productName                         |
+-------------------------------------+
| 1992 Porsche Cayenne Turbo Silver   |
| 1992 Ferrari 360 Spider red         |
| 2001 Ferrari Enzo                   |
| 1932 Alfa Romeo 8C2300 Spider Sport |
| 1948 Porsche 356-A Roadster         |
| 1948 Porsche Type 356 Roadster      |
| 1956 Porsche 356A Coupe             |
+-------------------------------------+
7 rows in set (0.00 sec)
```

Notice that blind query expansion tends to increase noise significantly by returning non-relevant results. It is highly recommended that you use query expansion only when the searched keyword is hort.

## ngram Full-Text parser

The built-in MySQL full-text parser determines the beginning and ending of words using white space. When it comes to ideographic languages such as Chinese, Japanese or Koren etc, this is a limitation because these languages do not use word delimiters.

To address this issue, MySQL provided the ngram full-text parser. Since version 5.7.6, MySQL included ngram full-text parser as a built-in server plugin, meaning that MySQL loads this plugin automatically when the MySQL database server starts. MySQL supports ngram full-text parser for both InnoDB and MyISAM storage engines.

By definition, angram is a contigous sequence of characyters from a sequence of text. The main function of ngram full-text parser is tokenizing a sequence of text into a contigous sequence of n characters.

The following illustrates how the ngram full-text parser tokenizes a sequence of text for  different value of n:

```sql
n = 1: 'm','y','s','q','l'
n = 2: 'my', 'ys', 'sq','ql' 
n = 3: 'mys', 'ysq', 'sql'
n = 4: 'mysq', 'ysql'
n = 5: 'mysql'
```

### Creating FULLTEXT indexes with ngram parser

To create a FULL TEXT index that uses ngram full-text parser, you add the `WITH PARSER ngram` in the CREATE TABLE, ALTER TABLE, or CREATE INDEX statement.

For example the following statements creates new posts table and adds the title and body columns to the FULLTEXT index that use ngram full-text parser.

```sql
CREATE TABLE posts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255),
    body TEXT,
    FULLTEXT ( title , body ) WITH PARSER NGRAM
)  ENGINE=INNODB CHARACTER SET UTF8MB4;

CREATE TABLE posts (
    id INT PRIMARY KEY AUTO_INCREMENT,
    title VARCHAR(255),
    body TEXT,
    FULLTEXT ( title , body ) WITH PARSER NGRAM
)  ENGINE=INNODB CHARACTER SET UTF8MB4;

SET GLOBAL innodb_ft_aux_table="test/posts";
 
SELECT 
    *
FROM
    information_schema.innodb_ft_index_cache
ORDER BY doc_id , position;

```

### Setting ngram token size

As you can see the previous example, the token size (n) in the ngram by default is 2. To change the token size, you use the `ngram_token_size` configuration option, which has a value between 1 and 10.

Note that a smaller token size makes smaller full-text index and allows you to search faster.

Because `ngram_token_size` is a read-only variable, therefore you only can set its value using two options

```sql
mysqld --ngram_token_size=1
```

```sql
[mysqld]
ngram_token_size=1
```

MySQL converts a phrase searc into ngram phrase searches. For examplem "abc" is converted into "ab bc", which returns documents that contain "ab bc" and "abc".

### processing search result with ngram

In `NATURAL LANGUAGE MODE` searches, the search term is converted to a union of ngram values. Suppose the token size is 2 or bigram, the search term `mysql` is converted to `my ys sq ql`.

In `BOOLEAN MODE` searches, the search term is converted to a ngram phrase search.

#### ngram wildcard search

The ngram `FULLTEXT` index contains only ngrams, therefore it does not know the beginning of terms. When you perform wildcard searches, it may return unexpected result.

The following rultes are applied to wildcard search using ngram `FULLTEXT` search indexes:

If the prefix term in the wildcard is shorter than ngram token size, the query returns all documents that contain ngram tokens starting with the prefix term.

```sql
SELECT 
    id, title, body
FROM
    posts
WHERE
    MATCH (title , body) AGAINST ('my*' );
```

In case the prefix term in the wildcard is longer than ngram token size, MySQL will convert the prefix term into ngram phrases and ignore the wildcard operator. 

```sql
SELECT 
    id, title, body
FROM
    posts
WHERE
    MATCH (title , body) AGAINST ('mysqld*' );
```

In this example, the term "mysqld" is converted into ngram phrases `"my" "ys" "sq" "ql" "ld"`. Therefore all documents that contain one of these phrases are returned.

#### Handling stopword

The ngram parser excludes tokens that contain the stopword in the stopword list. For example, suppose the `ngram_token_size` is 2 and document contains "abd". The ngram parser will tokenize the document to "ab" "bc". If "b" is a stopword, ngram will exclude both "ab" and "bc" because they contain "b".

Note that you must define your own stopword list if the language is other than English. In addition the stopwords with lengthhs that are greater than `ngram_token_size` are ignored.