# Introduction to SQL

## Datatypes in SQL

|    DataType     | Description                                                                           |
| :-------------: | :------------------------------------------------------------------------------------ |
|   `char(n) `    | A string with fixed length `n`                                                        |
|  `varchar(n) `  | A string with maximum length `n`                                                      |
|     `int `      | Integer                                                                               |
| `numeric(p, d)` | A number with maximum `p` digits with a maximum of `d` digits after the decimal point |
|   `float(n)`    | Floating point number with a precision of `n` digits                                  |

!!! tip

    Refer to [CheatSheet](/DBMS-Query-Cheatsheet) for quick access to most useful SQL commands.

## Additional Basic Operations/Commands

### Cartesian Product

Let us say you want cartesian product of two tables `A` and `B`. You can do it using the following SQL command:

```sql
SELECT * FROM A, B;
```

!!! failure Remember

    This will give all combinations between `A` and `B` ad some may not be meaningful.

    Example, if there is a table `A` with teacher names and table `B` with their departments. Then cartesian product will give all combinations of teacher names and departments and **not the department of each teacher**. You need to use `JOIN` or some **where-clause** for that purpose.

!!! warning

    For same attributes in both tables, the SQL will present them as `A.attribute` and `B.attribute`.

### `RENAME AS` Operation

In SQL you can assign an alias to a table as well as an attribute. The command to do this is

```sql
-- For attributes
SELECT A.attribute AS alias_name FROM A;

-- For table name
SELECT * FROM A AS alias_name;

-- You can also give multiple names to the same table
SELECT * FROM A AS alias_name1, A AS alias_name2;
```

You can now use the **alias** in the whole query.

!!! tip

    Keyword `AS` is optional in SQL. You can omit that and remodify the query to
    ```sql
    SELECT A.attribute alias_name FROM A;
    ```

### String Operations

To compare strings in SQL, you can use the **like** operator. The **like** operator uses patterns described by **two** special characters:

- `%` - The `%` operator is equivalent to any substring in the string.
- `_` - The `_` operator is equivalent to any single character in the string.

#### `%` operator

Let us define a dummy query that checks for name of teachers that contain the substring `ma` in their name.

```sql
SELECT *
FROM teachers
WHERE name LIKE '%ma%';
```

!!! note

    Here the first % operator says that any string can come before ma and the second % operator says that any string can come after ma.

If I modify the same query to

```sql
SELECT *
FROM teachers
WHERE name LIKE '%ma';
```

Now this will give the names of the teachers that contain the substring `ma` at the end of their name.

#### `_` operator

Let us say that I want to find the names of teachers that have exactly 6 characters in their last name and ends in `"ma"`. I can do this using the `_` operator.

```sql
SELECT name
FROM teachers
WHERE name LIKE '____ma';
```

#### Points to note for `string operations`

- Patterns are case sensitive.
- SQL also supports string concatenation using `||` operator.
- SQL also supports `convert to uppercase` and `convert to lowercase` operations.

### `ORDER BY` Operation

You can order the results by a particular attribute using the `ORDER BY` operation. The syntax is

```sql
SELECT attribute_name
FROM table_name
WHERE ....
ORDER BY attribute_name;
```

!!! warning

    The **attribute** you use in `ORDER BY` operation should be displayed in the query. You cannot use an attribute that is not displayed in the query, i.e., the column that is used in `ORDER BY` operation should be present in the `SELECT` clause.

### `IN` Operator

You can check whether an attribute value is in a set of values using the `IN` operator. The syntax is

Let us filter out all instructor from department 'Comp. Sci.' and 'Physics'.

```sql
SELECT *
FROM instructors
WHERE dept_name IN ('Comp. Sci.', 'Physics');
```

### `GROUP BY` Operator

You can group attributes based on a particular attribute using the `GROUP BY` operation. The syntax is

```sql
SELECT attribute_name
FROM table
WHERE ....
ORDER BY ...
GROUP BY attribute_name;
```

!!! failure Remember

    The **attribute** you use in `GROUP BY` operation should be displayed in the query. You cannot use an attribute that is not displayed in the query, i.e., the column that is used in `GROUP BY` operation should be present in the `SELECT` clause except the use of aggregate function.

## Set Operations

### UNION

Let us filter out all instructor from department 'Comp. Sci.' and 'Physics'.

```sql
SELECT name FROM instructor WHERE dept_name = 'Comp. Sci.'
UNION
SELECT name FROM instructor WHERE dept_name = 'Physics';
```

### INTERSECT

Let us filter out all instructor from department 'Comp. Sci.' after 2000.

```sql
SELECT name FROM instructor WHERE dept_name = 'Comp. Sci.'
INTERSECT
SELECT name FROM instructor WHERE join_date > '2000'
```

### EXCEPT

Let us filter out all instructor from department 'Physics' after 2000.

```sql
SELECT name FROM instructor WHERE dept_name = 'Physics'
EXCEPT
SELECT name FROM instructor WHERE join_date < '2000'
```

## NULL Values.

`NULL` values in SQL basically means that the values for the attribute has not been defined yet or the value does not exist yet. However, you can also assign **null** to attributes in SQL.

### Arithmetic Operations Involving `NULL`

You can peform arithmetic operations involving `NULL` values in SQL. The result of any arithmetic operation involving `NULL` is `NULL`.

### Comparing `NULL` values

You can compare `NULL` values in SQL. The result of any comparison involving `NULL` is `UNKNOWN`.

You can only use `IS NULL` and `IS NOT NULL` to check for `NULL` values.

### `NULL` and Boolean Algebra

#### `OR` Operator

- `NULL or true` returns `true`
- `NULL or false` returns `false`
- `NULL or NULL` returns `unknown`

### `AND` operator

- `NULL and true` returns `unknown`
- `NULL and false` returns `false`
- `NULL and NULL` returns `unknown`

### `NOT` operator

- `not NULL` returns `unknown`

!!! tip

    In SQL, `unknown` is treated as `false`.
