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


## MySQL Primary Key

A primary key in MySQL is a field or a combination of fields that uniquely identifies each record in a table. It ensures that the values in the specified column or columns are unique and cannot be null. Each table can have only one primary key, and it is a critical component for maintaining data integrity.

## Rules for Primary Key

1. **Uniqueness:** The primary key column(s) must contain unique values.
2. **Non-null:** The primary key column(s) cannot contain null or empty values.
3. **Single Primary Key:** A table can have only one primary key.
4. **Data Type:** It is recommended to use `INT` or `BIGINT` data types for primary key columns.
5. **AUTO_INCREMENT:** The primary key column can use the `AUTO_INCREMENT` attribute to automatically generate sequential values.

## Syntax for CREATE TABLE Statement

### For a single primary key column:

```sql
CREATE TABLE table_name (
    col1 datatype PRIMARY KEY,
    col2 datatype,
    ...
);
```

### For multiple primary key columns:

```sql
CREATE TABLE table_name (
    col1 col_definition,
    col2 col_definition,
    ...
    CONSTRAINT [constraint_name] PRIMARY KEY (column_name(s))
);
```

**Parameters:**
- **table_name:** The name of the table.
- **col1, col2:** Column names in the table.
- **constraint_name:** The name of the primary key.
- **column_name(s):** The column name(s) forming the primary key.

## Example

```sql
-- Example with a single primary key column
CREATE TABLE Login(
   login_id INT AUTO_INCREMENT PRIMARY KEY,
   username VARCHAR(40),
   password VARCHAR(55),
   email VARCHAR(55)
);

-- Example with multiple primary key columns
CREATE TABLE Students (
    Student_ID int,
    Roll_No int,
    Name varchar(45) NOT NULL,
    Age int,
    City varchar(25),
    Primary Key(Student_ID, Roll_No)
);
```

## Alter Table to Add Primary Key

To add a primary key using the `ALTER TABLE` statement:

```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_list);
```

**Example:**

```sql
ALTER TABLE Persons ADD PRIMARY KEY(Person_ID);
```

## Drop Primary Key

To drop the primary key from a table:

```sql
ALTER TABLE table_name DROP PRIMARY KEY;
```

**Example:**

```sql
ALTER TABLE Login DROP PRIMARY KEY;
```

## Primary Key vs. Unique Key

- **Primary Key:**
  - Uniquely identifies each record in a table.
  - Does not allow NULL values.
  - Only one primary key per table.
  - Creates a clustered index.

- **Unique Key:**
  - Identifies each row uniquely in the absence of a primary key.
  - Can accept only one NULL value.
  - A table can have more than one unique key.
  - Creates a non-clustered index.

Understanding and using primary keys is essential for ensuring data integrity and efficient database operations.


## MySQL Foreign Key

A foreign key in MySQL is used to establish a link between tables by referencing the primary key field of one table in another table. It is also known as a referencing key. The foreign key field in one table refers to the primary key field of another table, creating a parent-child relationship. This ensures referential integrity within the database.

MySQL allows the definition of a foreign key constraint on the child table, ensuring that the values in the foreign key column(s) match the primary key column(s) in the referenced parent table.

## MySQL Foreign Key Syntax

Foreign keys can be defined using the `CREATE TABLE` statement or added later using the `ALTER TABLE` statement.

### Using CREATE TABLE Statement:

```sql
CREATE TABLE child_table (
    column1 datatype,
    column2 datatype,
    ...
    CONSTRAINT [constraint_name] FOREIGN KEY (foreign_key_column(s))
    REFERENCES parent_table (parent_key_column(s))
    ON DELETE reference_option
    ON UPDATE reference_option
);
```

### Using ALTER TABLE Statement:

```sql
ALTER TABLE child_table
ADD CONSTRAINT [constraint_name] FOREIGN KEY (foreign_key_column(s))
REFERENCES parent_table (parent_key_column(s))
ON DELETE reference_option
ON UPDATE reference_option;
```

**Parameters:**
- **constraint_name:** The name of the foreign key constraint. If not provided, MySQL generates one automatically.
- **foreign_key_column(s):** The column(s) in the child table that act as foreign keys.
- **parent_table:** The name of the parent table containing the referenced primary key.
- **parent_key_column(s):** The column(s) in the parent table serving as the primary key.
- **reference_option:** Specifies how changes to the parent key affect the foreign key. Options include `CASCADE`, `SET NULL`, `RESTRICT`, `NO ACTION`, and `SET DEFAULT`.

## MySQL Foreign Key Example

Let's go through an example to understand how foreign keys work in MySQL.

Assume we have two tables, `customer` and `contact`. The `customer` table has a primary key `ID`, and the `contact` table has a foreign key `Customer_Id` referencing the `ID` in the `customer` table.

```sql
CREATE TABLE customer (
    ID INT NOT NULL AUTO_INCREMENT,
    Name VARCHAR(50) NOT NULL,
    City VARCHAR(50) NOT NULL,
    PRIMARY KEY (ID)
);

CREATE TABLE contact (
    ID INT,
    Customer_Id INT,
    Customer_Info VARCHAR(50) NOT NULL,
    Type VARCHAR(50) NOT NULL,
    INDEX par_ind (Customer_Id),
    CONSTRAINT fk_customer FOREIGN KEY (Customer_Id)
    REFERENCES customer(ID)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
```

In this example:
- The `customer` table has a primary key `ID`.
- The `contact` table has a foreign key `Customer_Id` referencing the `ID` in the `customer` table.
- The `ON DELETE CASCADE` and `ON UPDATE CASCADE` options ensure that corresponding rows in the `contact` table are deleted or updated when the referenced row in the `customer` table is deleted or updated.

## Foreign Key Checks

MySQL has a variable called `foreign_key_checks` that controls foreign key checking. By default, it is enabled to enforce referential integrity during normal operations. You can disable foreign key checks in scenarios like dropping a referenced table, importing data, or altering a table with a foreign key.

### Disable Foreign Key Checks:

```sql
SET foreign_key_checks = 0;
```

### Enable Foreign Key Checks:

```sql
SET foreign_key_checks = 1;
```

Disabling foreign key checks can be useful when you need to perform operations that might violate referential integrity temporarily.

## Dropping Foreign Key

To drop an existing foreign key, you can use the `ALTER TABLE` statement:

```sql
ALTER TABLE table_name DROP FOREIGN KEY fk_constraint_name;
```

Replace `table_name` with the name of your table and `fk_constraint_name` with the name of your foreign key constraint. If you don't know the foreign key constraint name, you can use `SHOW CREATE TABLE` to find it.

Understanding and using foreign keys is crucial for maintaining relationships between tables and ensuring data integrity in a relational database.
