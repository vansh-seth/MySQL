# MySQL Keys
## MySQL Unique Key

A unique key in MySQL ensures that all values stored in a column or a combination of columns are unique, preventing the storage of duplicate values. It is commonly used for fields like email addresses, roll numbers, or any other data that should be unique.

## Needs of Unique Key

- **Preventing Duplicates:** Ensures that identical values are not stored in the column.
- **Integrity and Reliability:** Maintains the integrity and reliability of the database by storing only distinct values.
- **Foreign Key Relationships:** Works with foreign keys to preserve the uniqueness of a table.
- **Null Values:** Can contain null values, but only one null value per column is allowed.

## Syntax

### For a single unique key column:

```sql
CREATE TABLE table_name(
    col1 datatype,
    col2 datatype UNIQUE,
    ...
);
```

### For multiple unique key columns:

```sql
CREATE TABLE table_name(
  col1 col_definition,
  col2 col_definition,
  ...
  [CONSTRAINT constraint_name]
  UNIQUE(column_name(s))
);
```

**Note:** If no name is specified for the unique constraint, MySQL generates a name automatically.

## Parameter Explanation

- **table_name:** The name of the table being created.
- **col1, col2:** Column names in the table.
- **constraint_name:** The name of the unique key.
- **column_name(s):** The column name(s) that form the unique key.

## Unique Key Example

```sql
-- Example with a single unique key column
CREATE TABLE Student2 (
    Stud_ID int NOT NULL UNIQUE,
    Name varchar(45),
    Email varchar(45),
    Age int,
    City varchar(25)
);

-- Example with multiple unique key columns
CREATE TABLE Student3 (
    Stud_ID int,
    Roll_No int,
    Name varchar(45) NOT NULL,
    Email varchar(45),
    Age int,
    City varchar(25),
    CONSTRAINT uc_rollno_email UNIQUE(Roll_No, Email)
);
```

## Drop Unique Key

To drop a unique key, you can use the `ALTER TABLE` statement:

```sql
ALTER TABLE table_name DROP INDEX constraint_name;
```

Example:

```sql
ALTER TABLE Student3 DROP INDEX uc_rollno_email;
```

## Unique Key Using ALTER TABLE Statement

To add a unique key using the `ALTER TABLE` statement:

```sql
ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE(column_list);
```

Example:

```sql
ALTER TABLE Student3 ADD CONSTRAINT uc_rollno_email UNIQUE(Roll_No, Email);
```

This statement allows modifying an existing table by adding a unique key to a column.

These unique key constraints help maintain data integrity and ensure a structured and organized approach to accessing information in a MySQL database.
