# Cheatsheet

### To create a table

```sql linenums="1"
CREATE table table_name(column_name_1 data_type constraint, column_name_2 data_type constraint)
```

!!! warning

    Add `primary` key after the `colum_name` if that column is primary.

### To select from a table

#### All columns

```sql
select * from table_name
```

#### Specific column

```sql
select column_name(s) from table_name
```

### To insert into table

```sql
insert into table_name values(all_values_seprated_by_comma)
```

!!! warning

    Note: `char` and `varchar` must be enclosed with single quotes(`'`)

### Creating keys

#### Primary key

Add the `primary key` keyword after the column_name.

!!! tip

    `primary key` declaration on an attribute ensures that the attribute is `not null`

#### Composite primary key

Add the `primary key (column_name_1, column_name_2, ....)` at the end before the closing parentheses `)` while creating the table.

#### Foreign key

Add the `foreign key (column_name) references parent_table(parent_column)`at the end before the closing parentheses `)` while creating the table.

### Deleting rows

```sql
delete from table_name where delete_condition(s)
```

### Alter

#### Adding an attribute

```sql
alter table table_name add attribute_name data_type
```

#### Deleting an attribute

```sql
alter table table_name drop attribute_name
```

### Important Points to Note

- `delete`: Delete row(s) from the table. But schema is not lost
- `drop`: Entire table is deleted along with schema.
- `truncate`: Deletes the table along with schema, but the schema is regenerated.
