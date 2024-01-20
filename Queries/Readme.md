## MySQL Common Queries Guide

Here's a guide to commonly used MySQL queries for creating databases, using databases, creating tables, inserting records, updating records, deleting records, selecting records, truncating tables, and dropping tables.

### 1) MySQL Create Database

MySQL `CREATE DATABASE` is used to create a new database.

**Example:**
```sql
CREATE DATABASE db1;
```

### 2) MySQL Select/Use Database

MySQL `USE DATABASE` is used to select a specific database.

**Example:**
```sql
USE db1;
```

### 3) MySQL Create Query

MySQL `CREATE` query is used to create a table, view, procedure, or function.

**Example:**
```sql
CREATE TABLE customers (
  id INT(10),
  name VARCHAR(50),
  city VARCHAR(50),
  PRIMARY KEY (id)
);
```

### 4) MySQL Alter Query

MySQL `ALTER` query is used to add, modify, delete, or drop columns of a table.

**Example:**
```sql
ALTER TABLE customers
ADD age VARCHAR(50);
```

### 5) MySQL Insert Query

MySQL `INSERT` query is used to insert records into a table.

**Example:**
```sql
INSERT INTO customers VALUES (101, 'rahul', 'delhi');
```

### 6) MySQL Update Query

MySQL `UPDATE` query is used to update records in a table.

**Example:**
```sql
UPDATE customers SET name='bob', city='london' WHERE id=101;
```

### 7) MySQL Delete Query

MySQL `DELETE` query is used to delete records from a table.

**Example:**
```sql
DELETE FROM customers WHERE id=101;
```

### 8) MySQL Select Query

MySQL `SELECT` query is used to fetch records from a table.

**Example:**
```sql
SELECT * FROM customers;
```

### 9) MySQL Truncate Table Query

MySQL `TRUNCATE TABLE` query is used to remove all records from a table.

**Example:**
```sql
TRUNCATE TABLE customers;
```

### 10) MySQL Drop Query

MySQL `DROP` query is used to drop a table, view, or database.

**Example:**
```sql
DROP TABLE customers;
```


## MySQL Constraints Guide

Constraints in MySQL are used to specify rules that allow or restrict what values/data can be stored in a table. They ensure data accuracy and integrity, helping to maintain consistency in the database. Constraints can be applied at either the column level or the table level.

### Types of MySQL Constraints

1. **Column Level Constraints:**
   - Applied to a single column.
  
2. **Table Level Constraints:**
   - Applied to the entire table.

### How to Create Constraints in MySQL

Constraints can be defined during table creation using the `CREATE TABLE` statement. The `ALTER TABLE` statement is used to specify constraints for existing table schemas.

#### Syntax
```sql
CREATE TABLE new_table_name (  
    col_name1 datatype constraint,  
    col_name2 datatype constraint,  
    col_name3 datatype constraint,  
    ...
);
```

### Common MySQL Constraints

1. **NOT NULL Constraint:**
   - Specifies that a column cannot have NULL values.
   ```sql
   CREATE TABLE Student(Id INTEGER, LastName TEXT NOT NULL, FirstName TEXT NOT NULL, City VARCHAR(35));
   ```

2. **UNIQUE Constraint:**
   - Ensures that all values in a column are unique.
   ```sql
   CREATE TABLE ShirtBrands(Id INTEGER, BrandName VARCHAR(40) UNIQUE, Size VARCHAR(30));
   ```

3. **CHECK Constraint:**
   - Controls the value in a column based on a given condition.
   ```sql
   CREATE TABLE Persons (  
       ID int NOT NULL,  
       Name varchar(45) NOT NULL,  
       Age int CHECK (Age>=18)  
   );
   ```

4. **DEFAULT Constraint:**
   - Sets a default value for a column if no value is specified.
   ```sql
   CREATE TABLE Persons (  
       ID int NOT NULL,  
       Name varchar(45) NOT NULL,  
       Age int,  
       City varchar(25) DEFAULT 'New York'  
   );
   ```

5. **PRIMARY KEY Constraint:**
   - Identifies each record in a table uniquely.
   ```sql
   CREATE TABLE Persons (  
       ID int NOT NULL PRIMARY KEY,   
       Name varchar(45) NOT NULL,   
       Age int,   
       City varchar(25)
   );
   ```

6. **AUTO_INCREMENT Constraint:**
   - Automatically generates a unique number when inserting a new record.
   ```sql
   CREATE TABLE Animals(
       id int NOT NULL AUTO_INCREMENT,
       name CHAR(30) NOT NULL,
       PRIMARY KEY (id)
   );
   ```

7. **ENUM Constraint:**
   - Limits the values for a column to a specified list.
   ```sql
   CREATE TABLE Shirts (
       id INT PRIMARY KEY AUTO_INCREMENT,
       name VARCHAR(35),
       size ENUM('small', 'medium', 'large', 'x-large')
   );
   ```

8. **INDEX Constraint:**
   - Speeds up data retrieval by creating an index for one or more columns.
   ```sql
   CREATE INDEX idx_name ON Shirts(name);
   ```

9. **FOREIGN KEY Constraint:**
   - Links two tables together, typically connecting a foreign key in one table to the primary key in another.
   ```sql
   CREATE TABLE Persons (
       Person_ID int NOT NULL PRIMARY KEY,
       Name varchar(45) NOT NULL,
       Age int,
       City varchar(25)
   );

   CREATE TABLE Orders (
       Order_ID int NOT NULL PRIMARY KEY,
       Order_Num int NOT NULL,
       Person_ID int,
       FOREIGN KEY (Person_ID) REFERENCES Persons(Person_ID)
   );
   ```

These constraints play a crucial role in maintaining data integrity and ensuring that the data in a MySQL database follows predefined rules.
