# Introduction to Relational Model

## Attributes

- The parameters in the database schema is known as **attributes.**
- The set of allowed values for the attribute is known as the **domain** of attribute.&#x20;
- Attribute values are conventionally preferred to be **atomic**
- `null` is a special value and is available in the domain of each attribute. It indicates that the value is **unknown**.
- The `null` value needs to be checked thoroughly since it may cause complications.

## Schema and Instance

- Schema: A basic template of the database.
- Instance: Actual data in the database.

### Schema

A schema is mathematically as a **relation**.&#x20;

If there are $n$ attributes say, $A_1, A_2, A_3, ..., A_n$. Then $R=(A_1, A_2, A_3, ...,A_n)$ is the relational schema.

$$
\text{Let } D_1 \text{ be domain of }A_1, D_2 \text{ be domain of } A_2, \text{ and so on}, \\ \ \\
\text{ Then each row of the relational database } R \subset D_1 \text{x }D_2 \text{x } D_3 ... \text{x }D_n
$$

> Thus each row is an $n$-tuple value $r \subset R$.

### Instance

A set of tuples formed using the **schema** is known as the **instance**.

Some properties of instance:

- It can be unordered.
- There can't be identical rows.

## Keys

Since we know that each row in the database is unique, we consider a set $K$ such that $K \subset R$.

### Superkey

Now $K$ is a superkey of $R$ is $K$ is sufficient enough to identify unique rows in the database for each possible relation $R$.

### Candidate key

Now if the <a href="#superkey">**superkey**</a> $K$ is minimal, i.e., no subset of $K$ is a key then $K$ becomes a candidate key.

### Primary key

One of the <a href="#candidate-key">**candidate key**</a> is selected to be the primary key

!!! tip "Choosing a primary key"

    While choosing a candidate key to be a primary key make sure that the primary key gives you some additional information.

### Surrogate key

A **surrogate key** is a synthetic key created when the data is not unique, hence it is not derived from the data itself.

### Foreign key

When referencing to another table the original table must contain a key known as **foreign key** that can be used as identifier for the **referenced** table.

### Compound key

When more than one attributes are combined to be used as key, then it is called a **compound** or **composite** key.

## Relational operators

### `SELECT` Operator

The `SELECT` operator selects some specific rows based on the condition given.

Let there be a relation $r$ already defined. Then the `SELECT` operator denoted using $\sigma_{\text{conditions}}(r)$ filters out the required rows based on the conditions given and gives them as output.

### `PROJECT` Operator

The `PROJECT` operator selects some specific columns based on the columns asked for.

Let there be a relation $r$ already defined. Then the `PROJECT` operator denoted using $\pi_{\text{columnnames}}(r)$ filters out the required columns based on the column_names given and removes the duplicate columns if left after the projection and gives them as output.

!!!tip

    It is sometimes used to retrieve the original relations from the cartesian product using the following formula: $r=\pi_r(r\text{ x }s)$

### `UNION` Operator

Gives you a `UNION` of two relations and returns only the unique rows after the operation. Denoted by $ \cup $

### `DIFFERENCE` Operator

Let us say that $X$ and $Y$ are two relation defined beforehand. Then the `DIFFERENCE` of $X$ and $Y$, i.e., $X-Y$ returns the rows that are present in $X$ and not in $Y$.

### `INTERSECTION` Operator

Let us say that $X$ and $Y$ are two relation defined beforehand. Then the `INTERSECTION` operator returns the rows that are common to both $X$ as well as $Y$. It is denoted using $\cap$.

!!! note

    $r\cap s = r - (r - s)$

### `RENAME` Operator

`RENAME` allows us to call a relation, by other name. It is denoted by $\rho_{\text{new name}}(\text{old name})$

!!! abstract

    You can compose several relational operators.

### `NATURAL JOIN` Operator

If two relations have some identical attributes, then `NATURAL JOIN` returns only the union of those rows where the identical attributes have the same values in all the relations. It is denoted using $\bowtie$.

Example: $r\bowtie s$

## Points to Note

- Each query input and output is a table.
- Data in the output table appears in atleast one of the input table.
- Relational algebra may not work for some complex calculations.

