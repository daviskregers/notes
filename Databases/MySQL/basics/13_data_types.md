# Data types

## Numeric types

```
Type        Description
TINYINT     A very small integer
SMALLINT    A small integer
MEDIUMINT   A medium-sized integer
INT         A standard integer
BIGINT	    A large integer
DECIMAL	    A fixed-point number
FLOAT	    A single-precision floating point number
DOUBLE	    A double-precision floating point number
BIT         A bit field
```

MySQL does not have the built-in `BOOLEAN` or `BOOL` data type. To represent boolean values, the MySQL uses the smallest integer type which is `TINYINT(1)`.

## String types

Can hold anything from plain text to binary data such as images or files. Strings can be compared and searched in pattern matching by using `LIKE` operator, regular expression and full text search.

```
Type	    Description
CHAR	    A fixed-length nonbinary (character) string
VARCHAR	    A variable-length non-binary string
BINARY	    A fixed-length binary string
VARBINARY   A variable-length binary string
TINYBLOB    A very small BLOB (binary large object)
BLOB        A small BLOB
MEDIUMBLOB  A medium-sized BLOB
LONGBLOB    A large BLOB
TINYTEXT    A very small non-binary string
TEXT        A small non-binary string
MEDIUMTEXT  A medium-sized non-binary string
LONGTEXT    A large non-binary string
ENUM        An enumeration; each column value may be assigned one enumeration member
SET         A set; each column value may be assigned zero or more SET members
```

## Date and time types

```
Type	    Description
DATE        A date value in CCYY-MM-DD format
TIME        A time value in hh:mm:ss format
DATETIME    A date and time value inCCYY-MM-DD hh:mm:ssformat
TIMESTAMP   A timestamp value in CCYY-MM-DD hh:mm:ss format
YEAR        A year value in CCYY or YY format
```

## Spatial data types

```
Type	            Description
GEOMETRY            A spatial value of any type
POINT               A point (a pair of X-Y coordinates)
LINESTRING          A curve (one or more POINT values)
POLYGON             A polygon
GEOMETRYCOLLECTION  A collection of GEOMETRYvalues
MULTILINESTRING     A collection of LINESTRINGvalues
MULTIPOINT          A collection of POINTvalues
MULTIPOLYGON        A collection of POLYGONvalues
```
