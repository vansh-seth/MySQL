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

