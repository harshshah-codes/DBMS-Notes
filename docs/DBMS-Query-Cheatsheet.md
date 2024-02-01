# Cheatsheet



### To create a table

`CREATE table table_name(column_name_1 data_type constraint, column_name_2 data_type constraint)`&#x20;

> &#x20;Add `primary` key after the `colum_name` if that column is primary.



### To select from a table

#### All columns

`select * from table_name`

#### Specific column

`select column_name(s) from table_name`



### To insert into table

`insert into table_name values(all_values_seprated_by_comma)`

> Note: `char` and `varchar `must be enclosed with single quotes(`'`)



### Creating keys

#### Primary key

Add the `primary key` keyword after the column\_name.

#### Composite primary key

Add the `primary key (column_name_1, column_name_2, ....)` at the end before the closing parentheses `)` while creating the table.

#### Foreign key

Add the `foreign key (column_name) references parent_table(parent_column)`at the end before the closing parentheses `)` while creating the table.

####

### Deleting rows

`delete from table_name where delete_condition(s)`



### Important Points to Note

* `delete`: Delete row(s) from the table. But schema is not lost
* `drop`: Entire table is deleted along with schema.
* `truncate`: Deletes the table along with schema, but the schema is regenerated.