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


### MySQL INSERT Statement with Date Example

Let's extend the examples to include inserting dates into a MySQL table. Assume we have a new table named `Events` with columns `EventID`, `EventName`, and `EventDate`. Here's how you can use the `INSERT INTO` statement to add records with date values:

```sql
-- Creating the Events table
CREATE TABLE Events (
    EventID INT NOT NULL AUTO_INCREMENT,
    EventName VARCHAR(50) NOT NULL,
    EventDate DATE,
    PRIMARY KEY (EventID)
);

-- Inserting single record with date
INSERT INTO Events (EventName, EventDate)
VALUES ('Meeting', '2022-01-20');

-- Inserting multiple records with dates
INSERT INTO Events (EventName, EventDate)
VALUES
    ('Conference', '2022-02-15'),
    ('Workshop', '2022-03-10'),
    ('Seminar', '2022-04-05');

-- Checking the inserted records
SELECT * FROM Events;
```

In this example:
- We created the `Events` table with three columns: `EventID`, `EventName`, and `EventDate`.
- We inserted single and multiple records into the `Events` table using the `INSERT INTO` statement.
- The `EventDate` column is of type `DATE`, and the date values are in the format 'YYYY-MM-DD'.
- The `SELECT * FROM Events;` statement is used to display the inserted records.

Remember to adjust the column names and data types according to your table structure. The examples provided assume a table structure with an auto-incremented ID, an event name, and a date.



## MySQL UPDATE Query
MySQL UPDATE query is a DML statement used to modify the data of the MySQL table within the database. In a real-life scenario, records are changed over some time. So, we need to make changes in the values of the tables also. To do so, it is required to use the UPDATE query.

- The UPDATE statement is used with the SET and WHERE clauses. The SET clause is used to change the values of the specified column. We can update single or multiple columns at a time.

- Syntax:
Following is a generic syntax of UPDATE command to modify data into the MySQL table:
```sql
UPDATE table_name     
SET column_name1 = new-value1,   
        column_name2=new-value2, ...    
[WHERE Clause]
```


### MySQL DELETE Statement

The `DELETE` statement in MySQL is used to remove records from a table based on specified conditions. It allows you to delete one or more rows from a table, and you can use the `WHERE` clause to specify the conditions for deletion.

**Syntax:**
```sql
DELETE FROM table_name
WHERE condition;
```

- **table_name:** The name of the table from which you want to delete records.
- **condition:** The condition that specifies which rows to delete. If omitted, all rows from the table will be deleted.

#### Examples:

1. **Delete a Specific Record:**
   
   To delete a record with a specific condition (e.g., employee with `emp_id` 107):
   ```sql
   DELETE FROM Employees
   WHERE emp_id = 107;
   ```

2. **Delete All Records:**

   To delete all records from a table:
   ```sql
   DELETE FROM Employees;
   ```
   *Note: Be cautious when using this, as it will delete all rows in the table.*

3. **Delete with `LIMIT` Clause:**

   To delete a limited number of rows, you can use the `LIMIT` clause. For example, to delete the first 3 employees ordered by name:
   ```sql
   DELETE FROM Employees
   ORDER BY name
   LIMIT 3;
   ```

4. **Delete Using `JOIN` Clause:**

   If you want to delete records from multiple tables simultaneously, you can use the `JOIN` clause. For instance, deleting records from Employees and Payment tables where `emp_id` is 102:
   ```sql
   DELETE Employees, Payment
   FROM Employees
   INNER JOIN Payment ON Employees.emp_id = Payment.emp_id
   WHERE Employees.emp_id = 102;
   ```

*Always ensure you have a backup before performing delete operations, especially when deleting a large number of records or when conditions are critical.*


### MySQL DELETE Statement Examples

In these examples, we'll use the "Employees" and "Payment" tables to demonstrate various use cases of the `DELETE` statement. Let's assume the tables contain the following data:

#### Employees Table:
| emp_id | name    | age | salary   |
|--------|---------|-----|----------|
| 101    | Alice   | 28  | 60000    |
| 102    | Bob     | 32  | 75000    |
| 103    | Charlie | 45  | 90000    |
| 104    | David   | 28  | 55000    |
| 105    | Emma    | 35  | 80000    |
| 106    | Frank   | 40  | 95000    |
| 107    | Grace   | 22  | 50000    |

#### Payment Table:
| emp_id | payment_date | amount   |
|--------|--------------|----------|
| 101    | 2022-01-01   | 5000     |
| 102    | 2022-01-01   | 6000     |
| 103    | 2022-01-01   | 7000     |
| 104    | 2022-01-01   | 4500     |
| 105    | 2022-01-01   | 5500     |
| 106    | 2022-01-01   | 8000     |
| 107    | 2022-01-01   | 4000     |

#### Example 1: Delete a Specific Record

To delete an employee with `emp_id` 107:
```sql
DELETE FROM Employees
WHERE emp_id = 107;
```

*After executing the query, verify the table using `SELECT * FROM Employees;`*

#### Example 2: Delete All Records from a Table

To delete all records from the "Employees" table:
```sql
DELETE FROM Employees;
```
*Be cautious when using this, as it will delete all rows in the table.*

#### Example 3: Delete with `LIMIT` Clause

To delete the first three employees ordered by name:
```sql
DELETE FROM Employees
ORDER BY name
LIMIT 3;
```

#### Example 4: Delete Using `JOIN` Clause

To delete records from Employees and Payment tables where `emp_id` is 102:
```sql
DELETE Employees, Payment
FROM Employees
INNER JOIN Payment ON Employees.emp_id = Payment.emp_id
WHERE Employees.emp_id = 102;
```

*Always ensure you have a backup before performing delete operations, especially when deleting a large number of records or when conditions are critical.*


### MySQL SELECT Statement

The `SELECT` statement in MySQL is used to retrieve data from one or more tables. It allows you to fetch records based on specified criteria, work with different scripting languages like PHP or Ruby, and handle various operations on data.

#### `SELECT` Statement Syntax

The general syntax of the `SELECT` statement is as follows:

```sql
SELECT field_name1, field_name2, ... field_nameN
FROM table_name1, table_name2, ...
[WHERE condition]
[GROUP BY field_name(s)]
[HAVING condition]
[ORDER BY field_name(s)]
[OFFSET M] [LIMIT N];
```

For selecting all fields:

```sql
SELECT * FROM tables
[WHERE conditions]
[GROUP BY fieldNames(s)]
[HAVING condition]
[ORDER BY fieldNames(s)]
[OFFSET M] [LIMIT N];
```

#### Parameters Explanation

- **field_name(s) or ***: Specifies one or more columns to be returned in the result set. The asterisk (*) returns all fields of a table.

- **table_name(s)**: The name of the tables from which data is to be fetched.

- **WHERE**: An optional clause that specifies conditions to filter and return only matched records.

- **GROUP BY**: An optional clause that groups data from multiple records based on one or more columns.

- **HAVING**: An optional clause that works with the GROUP BY clause, returning only those rows where the condition is TRUE.

- **ORDER BY**: An optional clause for sorting the records in the result set.

- **OFFSET**: An optional parameter that specifies from which row to start. The default is zero.

- **LIMIT**: An optional parameter that limits the number of returned records in the result set.

**Note**: MySQL evaluates the FROM clause first, and then the SELECT clause is evaluated.

### Example:

```sql
-- Select all fields from the "Employees" table where age is greater than 30, order by salary in descending order, and limit to 10 records.
SELECT *
FROM Employees
WHERE age > 30
ORDER BY salary DESC
LIMIT 10;
```

This example demonstrates the basic usage of the `SELECT` statement with a `WHERE` clause, `ORDER BY` for sorting, and `LIMIT` for restricting the number of returned records.



### MySQL SELECT Statement Example

Let's explore how the `SELECT` command works in MySQL with examples. Assume we have a table named `employee_detail` with the following data:

1. To retrieve a single column from the table, execute the following query:

```sql
SELECT Name FROM employee_detail;
```

Output:
```
+--------+
|  Name  |
+--------+
| Alice  |
| Bob    |
| Carol  |
| David  |
| Emma   |
+--------+
```

2. To query multiple columns from the table, use the following query:

```sql
SELECT Name, Email, City FROM employee_detail;
```

Output:
```
+--------+----------------------+--------+
|  Name  |        Email         |  City  |
+--------+----------------------+--------+
| Alice  | alice@email.com      | NY     |
| Bob    | bob@email.com        | LA     |
| Carol  | carol@email.com      | SF     |
| David  | david@email.com      | NY     |
| Emma   | emma@email.com       | LA     |
+--------+----------------------+--------+
```

3. To fetch data from all columns using an asterisk (*), execute:

```sql
SELECT * FROM employee_detail;
```

Output:
```
+--------+----------------------+--------+------------------+
|  Name  |        Email         |  City  |  Working_Hours   |
+--------+----------------------+--------+------------------+
| Alice  | alice@email.com      | NY     |        8         |
| Bob    | bob@email.com        | LA     |        6         |
| Carol  | carol@email.com      | SF     |        5         |
| David  | david@email.com      | NY     |        7         |
| Emma   | emma@email.com       | LA     |        4         |
+--------+----------------------+--------+------------------+
```

4. Using aggregate functions, HAVING clause, and GROUP BY, get the employee name, city, and total working hours for employees with more than 5 working hours:

```sql
SELECT Name, City, SUM(Working_Hours) AS "Total working hours"
FROM employee_detail
GROUP BY Name
HAVING SUM(Working_Hours) > 5;
```

Output:
```
+--------+--------+----------------------+
|  Name  |  City  |  Total working hours  |
+--------+--------+----------------------+
| Alice  |  NY    |           8            |
| David  |  NY    |           7            |
+--------+--------+----------------------+
```

5. Using JOIN, retrieve matching records from the `customer` and `orders` tables:

```sql
SELECT cust_name, city, order_num, order_date
FROM customer INNER JOIN orders
ON customer.cust_id = orders.cust_id
WHERE order_date < '2020-04-30'
ORDER BY cust_name;
```

Output:
```
+-----------+--------+-----------+------------+
| cust_name |  city  | order_num | order_date |
+-----------+--------+-----------+------------+
|   Alice   |   NY   |     101   | 2020-04-20 |
|   Bob     |   LA   |     102   | 2020-04-25 |
|   Carol   |   SF   |     103   | 2020-04-15 |
+-----------+--------+-----------+------------+
```


### MySQL INSERT INTO SELECT Example

Let's explore how the `INSERT INTO SELECT` statement works in MySQL with an example. First, we'll create a table named `person`:

```sql
CREATE TABLE person (
  id int AUTO_INCREMENT PRIMARY KEY,
  name varchar(45) NOT NULL,
  email varchar(45) NOT NULL,
  city varchar(25) NOT NULL
);
```

Next, we'll insert some data into the `person` table:

```sql
INSERT INTO person (id, name, email, city)
VALUES
  (1, 'Stephen', 'stephen@javatpoint.com', 'Texas'),
  (2, 'Joseph', 'Joseph@javatpoint.com', 'Alaska'),
  (3, 'Peter', 'Peter@javatpoint.com', 'Texas'),
  (4, 'Donald', 'donald@javatpoint.com', 'New York'),
  (5, 'Kevin', 'kevin@javatpoint.com', 'Texas');
```

Now, suppose we want to insert the details of persons who belong to the 'Texas' city into another table named `person_info`. We'll first create the `person_info` table:

```sql
CREATE TABLE person_info (
  person_id int AUTO_INCREMENT PRIMARY KEY,
  person_name varchar(45) NOT NULL,
  email varchar(45) NOT NULL,
  city varchar(25) NOT NULL
);
```

Now, we'll use the `INSERT INTO SELECT` statement to achieve this:

```sql
INSERT INTO person_info (person_name, email, city)
SELECT name, email, city
FROM person
WHERE city = 'Texas';
```

If we want to insert all data from the `person` table into the `person_info` table without filtering, we can use the following statement:

```sql
INSERT INTO person_info
SELECT * FROM person;
```

These examples illustrate how the `INSERT INTO SELECT` statement allows us to copy data from one table to another based on specified conditions or all data from one table to another without filtering.

