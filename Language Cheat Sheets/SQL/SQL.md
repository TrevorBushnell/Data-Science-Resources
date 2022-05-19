# SQL Cheat Sheet


## What is SQL

* Structured Querying Language
* language that is used to get data from a database



### Structure of a SQL Environment

* **SERVERS:** the compute that contains your database(es). Typically the highest level of "container" for databases
* **DATABASES:** Collection of schemas and tables we can interact with
* **SCHEMA:** highest level of organization in databases - can contain multiple tables
* **TABLES:** Collection of rows/columns that contain the data that you are looking for



### Different Database Types

There are many different types of SQL servers/flavors that you can use

* MySQL (open source, Oracle)
* SQL Server (Microsoft)
* PostgreSQL (open source)
* Oracle Database (created by Oracle)
* SQL Lite



## SQL Data Types

* TEXT TYPES: Used to store text, can even store numbers as text
  * CHAR - must all be the same length
    * more like strings in Python/C++
  * VARCHAR - can have up to 255 characters
  * TEXT - Lots of words combined together
*  NUMERICAL TYPES: Used to store numbers
  * INTEGER
  * FLOAT
  * REAL
  * NUMERIC
  * BOOL
  * BOOLEAN - True/False value
* DATE TYPES: Used to store dates and times
* BINARY TYPES: Large files stored using 1's and 0's
  * TINYBLOB
  * BLOB



## Basic Querying

### `SELECT`

* Most basic query, used to pull data from a database

```sql
SELECT *
FROM dataset_1;
```

* `SELECT *` is the command
  * You can replace the `*` with the specific column name(s) that you want to work with
* `FROM dataset_1` tells the database which table to pull the data from
  * `dataset_1` is the table you are pulling from


### `LIMIT`
* Can be used to limit the amount of data that is pulled into a query
  * Useful for first exploring the data

```sql
LIMIT 10
```
* This makes a query and gets the first 10 entries

### `DISTINCT`
* Gets only the unique values from a column

```sql
SELECT DISTINCT passanger
FROM dataset_1;
```

### `WHERE`

* Statement that helps with filtering data however you would like

```sql
SELECT *
FROM dataset_1
WHERE destination = 'Home'
AND passanger = 'Alone'; 
```
* We can add more `WHERE` statements by using `AND` and `OR` commands

### `ORDER BY`

* Sorts the query you make based on a certain column

```sql
SELECT *
FROM dataset_1
WHERE passanger = 'Alone'
OR time = '2PM'
ORDER BY time;
```

* `DESC`: Sort in descending order

* `ASC`: Sort in ascending order



### Aliasing

* Gives a new name to the column/dataset that you want when you make the query

```sql
SELECT passanger, time as 'The Time'
```



### Comments

```sql
SELECT * -- This is a comment
```



## Aggregations

### `GROUP BY`

* Statement that groups results of the same value together
* Similar to distinct, however I can do other operations, like get the average of another column for each unique value in the column you grouped by

```sql
SELECT destination, AVG(temperature)
FROM dataset_1
GROUP BY destination;
```

* You will get the average temperature for each unique destination by running this code



### `AVG`

* Statement that takes the average of the data you query

```sql
SELECT weather, AVG(temperature) AS 'avg_temp'
FROM dataset_1
GROUP BY weather;
```



### `SUM`

* Statement used to sum the data that you query

```sql
SELECT weather, AVG(temperature), SUM(counts)
FROM dataset_1
GROUP BY weather;
```



### `COUNT`

* Statement used to count the number of occurrences from the data that you pull
