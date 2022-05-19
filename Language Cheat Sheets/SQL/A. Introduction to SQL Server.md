# Introduction to SQL Server

## 1. SELECTion Box

### 1.1: Welcome

* `SELECT`: key term from retrieving data
  * Can select multiple columns by separating column names by commas
  * Use `*` to get everything
    * not good for large tables
* `FROM`: key term for indicating where you want to get the data
* keywords will be in UPPERCASE and names will be in lowercase
* `TOP(X)`: returns X number of rows
* `AS`: Alias names with different names of your choosing
* `DISTINCT`: returns only unique rows



### 1.2: Ordering and Filtering

* Results are generally are returned as tabular data, but not always!
  * Can also get sets
* `ORDER BY`: sort the values returned by the indicated column(s)
  * `DESC` to do descending order
* Ordering strings does them alphabetically
* `WHERE`: ensure that we only return rows that meet our desired criteria
* `<>` is nonequality
* `BETWEEN`/`AND`: return values in a range
* `NULL`: no value for a particular field/record, help highlight gaps in our data



### 1.3: `WHERE` The Wild Things Are

* You can have multiple `WHERE` statements by using logic with `AND`, `OR`, `NOT`, etc.
* Make sure to watch your parentheses when you are writing more complex logic!
* To filter songs starting with certain letters, do `LIKE "a%"`





## 2: Groups, Strings, and Counting Things

### 2.1: Aggregating Data

* `SUM()`: sum the values in the indicated column
  * add  multiple columns by having multiple sum calls
* `COUNT()`: count the number of rows in a particular column
  * can use other keywords inside to count different values
* `MAX()`/`MIN()`: get the max/min value from a column
* `AVG()`: compute the average value in a column



### 2.2: Strings

* `LEN()` find the length of a string
* `LEFT([col_name], x)` get the `x` number of characters from `[col_name]` from the left
* `RIGHT([col_name], x)` get the `x` number of characters from `[col_name]` from the right
* `CHARINDEX(char, col_name)` find the index of `char` for the values in `col_name`
* `SUBSTRING(col_name, start_idx, num_char)`: get `num_char` of characters starting at `start_idx`
* `REPLACE(col_name, char1, char2)` replace every instance of `char1` with `char2`



### 2.3: Grouping and Having

* `GROUP BY`: group by the unique values in a given column
* `HAVING`: group by with given conditions, filters on groups whereas `WHERE` clauses filter on rows



## 3: Joining Tables

### 3.1: Joining Tables

* primary key: uniquely identify rows in a table
* foreign key: keys from different tables that you can link using joins
* **Inner Join:** Match rows with the same foreign keys from different tables
  * use keywords `INNER JOIN` and `ON`



## 3.2: Left and Right Join

* **Outer Join**: Matching all rows
  * *Left*: Work from table1 to table2
    * `LEFT JOIN` + `ON`
  * *Right*: Work from table2 to table1
    * `RIGHT JOIN` + `ON`
* TL;DR -> Inner joins only return matching rows, while outer joins return all rows from the main table plus matches from the joining table
  * There will be a NULL if there is no match in the 
* Left joins are more common

![image-20220509001010870](C:\Users\bushn\AppData\Roaming\Typora\typora-user-images\image-20220509001010870.png)



### 3.3: `UNION` & `UNION ALL`

* To combine queries into one table, use `UNION`
  * This will remove duplicate rows
* `UNION ALL` returns all rows including duplicates
* If combining data from different tables...
  * select same # of col in same order
  * cols should have same data types
* If source tables have different col names...
  * alias col names
* `UNION` removes duplicates (slower)
* `UNION ALL` does not remove duplicates (faster)23



## 4: You've Got the Power

### 4.1: Creator

* CRUD Operations
  * Create
  * Read
  * Update
  * Delete
* `CREATE TABLE` creates a new table

```sql
CREATE TABLE test_table(
test_date date,
test_name varchar(20),
test_int int
)
```

* Various data types in SQL
  * dates/datetimes
  * numeric
    * int, decimal, float
  * strings
    * car, varchar, nvarchar



### 4.2: Insert, Update, Delete

* `INSERT INTO` inserts into the table name

```sql
INSERT INTO table_name (col1, col2, col3)
VALUES
('value1', 'value2', value3)
```

* `INSERT SELECT` inserts data from a source table (can also apply some `WHERE` conditions)
  * Don't use `SELECT *`
  * Be specific in case table structure changes

* `UPDATE` update a value in the table
* `SET` indicate which column you want to set values for
* Don't forget a `WHERE` statement!

* `DELETE` deletes values from a table (`WHERE`!)



### 4.3: Declare Yourself

* **Variables**: a placeholder of a specific value of a specific type
* Create variable names with `@`
* `DECLARE @[var_name] [DATA_TYPE]` declare a variable
* Set variables with the `SET` keyword
* You can create temporary tables using `#`
  * temp tables can be used for the remainder of your sql session
