## MySQL CREATE TABLE

In MySQL, you can create a table using the `CREATE TABLE` statement. Below is the generic syntax for creating a table:

```sql
CREATE TABLE [IF NOT EXISTS] table_name (
    column_definition1,
    column_definition2,
    ...,
    table_constraints
);
```

- `table_name`: The name of the new table. It should be unique in the selected MySQL database. The `IF NOT EXISTS` clause avoids an error if the table already exists.
- `column_definition`: Specifies the name of each column along with its data type and other attributes such as NULL or NOT NULL.
- `table_constraints`: Specifies table constraints like PRIMARY KEY, UNIQUE KEY, FOREIGN KEY, CHECK, etc.

### Example

Let's create a table named "employee_table" in the "employeedb" database with the following columns: id, name, occupation, and age.

```sql
CREATE TABLE employee_table (
    id INT NOT NULL AUTO_INCREMENT,
    name VARCHAR(45) NOT NULL,
    occupation VARCHAR(35) NOT NULL,
    age INT NOT NULL,
    PRIMARY KEY (id)
);
```

**Note:**
- `NOT NULL` is used to specify that a field cannot be NULL.
- `AUTO_INCREMENT` is used to automatically add the next available number to the id field.
- `PRIMARY KEY` is used to define a column's uniqueness.

Visual representation of creating a MySQL table:

![image](https://github.com/vansh-seth/MySQL/assets/111755254/54429623-fe51-4ef2-8f71-8fbfac41b653)

To see the newly created table, use the following command:

```sql
SHOW TABLES;
```

To see the structure or information of the newly created table, use the following command:

```sql
DESCRIBE employee_table;
```

![image](https://github.com/vansh-seth/MySQL/assets/111755254/269b0db8-5045-4272-b645-68299f45da5e)


This will display the details of the "employee_table" including column names, data types, and constraints.

## MySQL ALTER Table

The `ALTER TABLE` statement in MySQL is used to modify an existing table. This can involve adding or dropping columns, modifying column definitions, or renaming columns or the entire table. Below are examples of various modifications you can make using `ALTER TABLE`.

### 1) ADD a Column in the Table

To add a new column, you can use the `ADD` command:

```sql
ALTER TABLE cus_tbl
ADD cus_age varchar(40) NOT NULL;
```

### 2) Add Multiple Columns in the Table

You can add multiple columns in a single `ALTER TABLE` statement:

```sql
ALTER TABLE cus_tbl
ADD cus_address varchar(100) NOT NULL AFTER cus_surname,
ADD cus_salary int(100) NOT NULL AFTER cus_age;
```

### 3) MODIFY Column in the Table

Use the `MODIFY` command to change the column definition:

```sql
ALTER TABLE cus_tbl
MODIFY cus_surname varchar(50) NULL;
```

### 4) DROP Column in the Table

To remove a column from a table, you can use the `DROP COLUMN` command:

```sql
ALTER TABLE cus_tbl
DROP COLUMN cus_address;
```

### 5) RENAME Column in the Table

To rename a column, use the `CHANGE COLUMN` command:

```sql
ALTER TABLE cus_tbl
CHANGE COLUMN cus_surname cus_title varchar(20) NOT NULL;
```

### 6) RENAME Table

To rename the entire table, use the `RENAME TO` command:

```sql
ALTER TABLE cus_tbl
RENAME TO cus_table;
```

These statements demonstrate various modifications that can be made to a MySQL table using the `ALTER TABLE` statement. Modify them as needed for your specific use case.

## MySQL Show/List Tables

In MySQL, the `SHOW TABLES` command is used to display the list of tables in the selected database. Here's an overview of how to use it:

1. Open the MySQL Command Line Client and log in to the MySQL database server.

   ```sql
   mysql -u your_username -p
   ```

2. Choose the specific database using the `USE` command.

   ```sql
   USE mystudentdb;
   ```

3. Execute the `SHOW TABLES` command.

   ```sql
   SHOW TABLES;
   ```

   This will display the list of tables in the selected database.

   ```sql
   +----------------------+
   | Tables_in_mystudentdb |
   +----------------------+
   | students             |
   | courses              |
   | grades               |
   +----------------------+
   ```

### Show Tables Using Pattern Matching

You can use the `LIKE` clause with the `SHOW TABLES` command to filter the returned tables based on a pattern.

```sql
SHOW TABLES LIKE "stud%";
```

This command will display tables whose names start with "stud".

### Show Tables in a Different Database

To list tables from a different database without switching to it, you can use the `IN` or `FROM` clause followed by the database name.

```sql
SHOW TABLES IN another_database;
-- OR
SHOW TABLES FROM another_database;
```

### Show Tables Using WHERE Clause

The `WHERE` clause can be used to filter tables based on specific conditions.

```sql
SHOW TABLES FROM sakila WHERE table_type = "VIEW";
```

This command will display only the views in the `sakila` database.

```sql
SHOW TABLES IN mystudentdb WHERE Tables_in_mystudentdb = "employees";
```

This command will display the table named "employees" in the `mystudentdb` database.

These variations of the `SHOW TABLES` command provide flexibility in listing and filtering tables based on different criteria.

In MySQL, you can rename a table using either the `RENAME TABLE` statement or the `ALTER TABLE` statement. The examples below demonstrate both methods:

1. **Using `RENAME TABLE` Statement:**

   Suppose you have a table named `employee`, and you want to rename it to `customer`. You can execute the following query:

   ```sql
   RENAME TABLE employee TO customer;
   ```

   This will rename the table `employee` to `customer`.

2. **Using `ALTER TABLE` Statement:**

   The `ALTER TABLE` statement can also be used to rename an existing table. The syntax is as follows:

   ```sql
   ALTER TABLE old_table_name RENAME TO new_table_name;
   ```

   If you want to rename the table `garments` to `shirts`, you can execute:

   ```sql
   ALTER TABLE garments RENAME TO shirts;
   ```

   This will rename the table `garments` to `shirts`.

3. **Renaming Temporary Table:**

   If you have a temporary table and want to rename it, you can use the `ALTER TABLE` statement as the `RENAME TABLE` statement doesn't support renaming temporary tables directly.

   ```sql
   CREATE TEMPORARY TABLE Students (
       name VARCHAR(40) NOT NULL,
       total_marks DECIMAL(12,2) NOT NULL DEFAULT 0.00,
       total_subjects INT UNSIGNED NOT NULL DEFAULT 0
   );

   -- Insert values into the temporary table

   -- Rename the temporary table using ALTER TABLE
   ALTER TABLE Students RENAME TO student_info;
   ```

   This will rename the temporary table `Students` to `student_info`.

Both methods allow you to change the name of a table in MySQL. Choose the one that suits your needs and the specific context in which you are working.

## MySQL Table Description Guide

## Steps

### 1. Switch to a Specific Database

Choose the database for which you want to describe the table:

```sql
USE your_database_name;
```

### 2. Execute DESCRIBE Statement

Execute the `DESCRIBE` statement for a specific table. Replace `your_table_name` with the actual name of the table you want to describe:

```sql
DESCRIBE your_table_name;
```

Alternatively, you can use the shorter `DESC` command:

```sql
DESC your_table_name;
```

The output will provide information about the columns in the specified table, including the column name, data type, whether it allows NULL values, key information, and more.

## MySQL DROP TABLE Guide

This guide provides instructions on how to use the `DROP TABLE` statement in MySQL to delete an existing table from the database.

## Syntax

The basic syntax for the `DROP TABLE` statement is as follows:

```sql
DROP TABLE table_name;
```

You can also include the optional `IF EXISTS` clause to avoid errors if the table does not exist:

```sql
DROP TABLE IF EXISTS table_name;
```

## Parameters

- **TEMPORARY**: An optional parameter that specifies to delete temporary tables only.
- **table_name**: Specifies the name of the table to be removed.
- **IF EXISTS**: Optional. Used to remove the table only if it exists in the database.
- **RESTRICT and CASCADE**: Both are optional parameters and do not have any impact on this statement. They are included in the syntax for future versions of MySQL.

## Example

Suppose we have a table named "orders" that we want to remove from the database. We can use the following command:

```sql
DROP TABLE orders;
```

This will permanently delete the table. You can also use the `IF EXISTS` clause to avoid errors if the table doesn't exist:

```sql
DROP TABLE IF EXISTS orders;
```

Make sure you have the necessary privileges to execute the `DROP TABLE` statement in MySQL.

**Note:** Be cautious when using this statement, as it permanently removes the table and its data.

## MySQL Temporary Tables Guide

MySQL provides a feature called Temporary Tables that allows users to store temporary data for the duration of a session. These tables are useful for complex tasks and can be accessed only within the current session. This guide explains how to create, use, and drop temporary tables in MySQL.

## Creating a Temporary Table

To create a temporary table, you can use the `CREATE TEMPORARY TABLE` statement. The syntax is similar to creating a regular table:

```sql
CREATE TEMPORARY TABLE table_name (
    column_1 datatype,
    column_2 datatype,
    ...
);
```

If you want to create a temporary table with the same structure as an existing table, you can use:

```sql
CREATE TEMPORARY TABLE temporary_table_name SELECT * FROM existing_table LIMIT 0;
```

## Inserting Data into a Temporary Table

After creating a temporary table, you can insert data into it using the `INSERT INTO` statement, similar to a regular table:

```sql
INSERT INTO temporary_table_name (column1, column2, ...)
VALUES (value1, value2, ...),
       (value1, value2, ...),
       ...;
```

## Querying Data from a Temporary Table

You can perform queries on temporary tables just like regular tables. For example:

```sql
SELECT * FROM temporary_table_name;
```

## Dropping a Temporary Table

To drop a temporary table, use the `DROP TEMPORARY TABLE` statement:

```sql
DROP TEMPORARY TABLE table_name;
```

It's recommended to use the `TEMPORARY` keyword to avoid accidentally dropping a permanent table with the same name.

## Example

Here's an example of creating, inserting data, querying, and dropping a temporary table:

```sql
-- Create a temporary table
CREATE TEMPORARY TABLE temp_students (
    student_name VARCHAR(40) NOT NULL,
    total_marks DECIMAL(12, 2) NOT NULL DEFAULT 0.00,
    total_subjects INT UNSIGNED NOT NULL DEFAULT 0
);

-- Insert data
INSERT INTO temp_students (student_name, total_marks, total_subjects)
VALUES ('Joseph', 150.75, 2),
       ('Peter', 180.75, 2);

-- Query data
SELECT * FROM temp_students;

-- Drop the temporary table
DROP TEMPORARY TABLE temp_students;
```

Remember that temporary tables are automatically dropped when the session ends.



## MySQL Column Operations Guide

## Adding a Column

To add a new column to an existing table in MySQL, you can use the `ALTER TABLE ADD COLUMN` statement. Here's the basic syntax:

```sql
ALTER TABLE table_name
    ADD COLUMN column_name column_definition [FIRST | AFTER existing_column];
```

- `table_name`: Name of the table you want to modify.
- `column_name`: Name of the new column.
- `column_definition`: Data type and definition of the new column.
- `FIRST` | `AFTER existing_column`: Optional. Specifies where in the table to create the new column.

### Example

```sql
-- Add a new column 'City' to the 'Test' table
ALTER TABLE Test
    ADD COLUMN City VARCHAR(30) NOT NULL;

-- Add 'Phone_number' after the 'Name' column
ALTER TABLE Test
    ADD COLUMN Phone_number VARCHAR(20) NOT NULL AFTER Name;
```

## Renaming a Column

To rename a column in MySQL, use the `ALTER TABLE CHANGE COLUMN` statement:

```sql
ALTER TABLE table_name
    CHANGE COLUMN old_column_name new_column_name column_definition [FIRST | AFTER existing_column];
```

- `table_name`: Name of the table.
- `old_column_name`: The current name of the column.
- `new_column_name`: The new name for the column.
- `column_definition`: Definition of the column (including data type).
- `FIRST` | `AFTER existing_column`: Optional. Specifies the position of the column.

### Example

```sql
-- Rename 'Phone_number' to 'Mobile_number' in the 'Test' table
ALTER TABLE Test
    CHANGE COLUMN Phone_number Mobile_number VARCHAR(20) NOT NULL;
```

## Deleting a Column

To remove a column from a MySQL table, use the `ALTER TABLE DROP COLUMN` statement:

```sql
ALTER TABLE table_name
    DROP COLUMN column_name;
```

- `table_name`: Name of the table.
- `column_name`: Name of the column to be deleted.

### Example

```sql
-- Remove 'Branch' column from the 'Test' table
ALTER TABLE Test
    DROP COLUMN Branch;

-- Remove multiple columns 'Mobile_number' and 'Email'
ALTER TABLE Test
    DROP COLUMN Mobile_number,
    DROP COLUMN Email;
```

## Important Considerations

- Deleting a column affects associated objects like triggers, stored procedures, and views.
- Changes in a table's schema may require updates in dependent applications' code.
- Deleting columns from large tables can impact database performance during the deletion process.

Always consider these factors before performing column operations in MySQL.



## MySQL Rename Column

Sometimes, it becomes necessary to rename or change the column names in a MySQL table. MySQL provides two ways to achieve this: using the `CHANGE` statement and using the `RENAME` statement. Below, you'll find a guide on how to perform these operations.

## Using the `CHANGE` Statement

To rename a column using the `CHANGE` statement, use the following syntax:

```sql
ALTER TABLE table_name
CHANGE COLUMN old_column_name new_column_name Data_Type;
```

- `table_name`: Name of the table.
- `old_column_name`: Current name of the column.
- `new_column_name`: New name for the column.
- `Data_Type`: Data type of the column.

### Example

Suppose we have a table named `balance` with a column `account_num`:

```sql
ALTER TABLE balance
CHANGE COLUMN account_num account_no VARCHAR(25);
```

## Using the `RENAME` Statement

To rename a column using the `RENAME` statement, use the following syntax:

```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name TO new_column_name;
```

- `table_name`: Name of the table.
- `old_column_name`: Current name of the column.
- `new_column_name`: New name for the column.

### Example

Suppose we have a table named `customer` with a column `account`:

```sql
ALTER TABLE customer
RENAME COLUMN account TO account_no;
```

## Renaming Multiple Columns

MySQL also allows renaming multiple columns within a single statement. You can use either the `CHANGE` statement or the `RENAME` statement for this purpose:

### Using `CHANGE` Statement

```sql
ALTER TABLE table_name
CHANGE old_column_name1 new_column_name1 Data_Type,
CHANGE old_column_name2 new_column_name2 Data_Type,
...,
CHANGE old_column_nameN new_column_nameN Data_Type;
```

### Using `RENAME` Statement

```sql
ALTER TABLE table_name
RENAME COLUMN old_column_name1 TO new_column_name1,
RENAME COLUMN old_column_name2 TO new_column_name2,
...,
RENAME COLUMN old_column_nameN TO new_column_nameN;
```

### Example

Suppose we want to change column names `id` and `customer_name` from the `customer` table:

```sql
-- Using CHANGE statement
ALTER TABLE customer
CHANGE id cust_id int,
CHANGE customer_name cust_name varchar(45);
```

```sql
-- Using RENAME statement
ALTER TABLE customer
RENAME COLUMN cust_id TO id,
RENAME COLUMN cust_name TO customer_name;
```

## MySQL View

In MySQL, a view is a virtual table based on the result of a SELECT query. Views allow you to simplify complex queries and encapsulate logic by creating a virtual table that can be queried like a regular table. This guide will cover creating, updating, and dropping views in MySQL.

## Creating a View

To create a view in MySQL, you can use the `CREATE VIEW` statement followed by a `SELECT` query. The basic syntax is as follows:

```sql
CREATE [OR REPLACE] VIEW view_name AS
SELECT columns
FROM tables
[WHERE conditions];
```

- **`OR REPLACE` (optional):** It is used when a view already exists. If specified, it replaces the existing view. If not specified and the view exists, an error is returned.

- **`view_name`:** The name of the view you want to create.

- **`columns`:** The columns you want to include in the view.

- **`tables`:** The source tables from which you are selecting data for the view.

- **`WHERE conditions` (optional):** Conditions to filter data in the view.

### Example:

Let's create a view named `trainer` based on the `courses` table:

```sql
CREATE VIEW trainer AS
SELECT course_name, trainer
FROM courses;
```

To view the created view, you can use:

```sql
SELECT * FROM trainer;
```

## Updating a View

To update the definition of an existing view, you can use the `ALTER VIEW` statement. This allows you to modify the columns, source tables, or conditions of the view.

```sql
ALTER VIEW view_name AS
SELECT columns
FROM tables
WHERE conditions;
```

### Example:

Let's update the `trainer` view by adding a new column:

```sql
ALTER VIEW trainer AS
SELECT id, course_name, trainer
FROM courses;
```

## Dropping a View

To delete an existing view, you can use the `DROP VIEW` statement.

```sql
DROP VIEW [IF EXISTS] view_name;
```

- **`IF EXISTS` (optional):** If specified, it prevents an error from occurring if the view does not exist.

### Example:

To drop the `trainer` view:

```sql
DROP VIEW trainer;
```

## Creating a View with JOIN Clause

You can create more complex views involving multiple tables and using a `JOIN` clause. In this example, we'll create a view named `Trainer` by joining the `courses` and `contact` tables:

```sql
CREATE VIEW Trainer AS
SELECT c.course_name, c.trainer, t.email
FROM courses c
JOIN contact t ON c.id = t.id;
```

Now you can query the `Trainer` view just like any other table:

```sql
SELECT * FROM Trainer;
```


