# MySQL JOINS

MySQL JOINS are used with the SELECT statement to retrieve data from multiple tables. They are performed whenever you need to fetch records from two or more tables.

There are three types of MySQL joins:

1. MySQL INNER JOIN (or sometimes called simple join)
2. MySQL LEFT OUTER JOIN (or sometimes called LEFT JOIN)
3. MySQL RIGHT OUTER JOIN (or sometimes called RIGHT JOIN)

## MySQL Inner JOIN (Simple Join)

The MySQL INNER JOIN is used to return all rows from multiple tables where the join condition is satisfied. It is the most common type of join.

**Syntax:**

```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

**Image representation:**

![image](https://github.com/vansh-seth/MySQL/assets/111755254/688aa8c0-e7ee-4ccc-b582-fcaa8d88fe20)


**Example:**

Consider two tables "officers" and "students", having the following data.

| officers       |          | students       |          |
| -------------- | -------- | -------------- | -------- |
| officer_id     | officer_name | student_id   | student_name | course_name |
| 1              | John Doe   | 1            | Alice       | Math        |
| 2              | Jane Smith | 2            | Bob         | English     |

Execute the following query:

```sql
SELECT officers.officer_name, officers.address, students.course_name
FROM officers
INNER JOIN students
ON officers.officer_id = students.student_id;
```

**Output:**

| officer_name | address   | course_name |
| ------------ | --------- | ----------- |
| John Doe     | [address] | Math        |
| Jane Smith   | [address] | English     |

## MySQL Left Outer Join

The LEFT OUTER JOIN returns all rows from the left-hand table specified in the ON condition and only those rows from the other table where the join condition is fulfilled.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT [OUTER] JOIN table2
ON table1.column = table2.column;
```

**Image representation:**

![image](https://github.com/vansh-seth/MySQL/assets/111755254/408347c4-16b0-4e82-943d-093c526b20d7)

**Example:**

Consider two tables "officers" and "students", having the following data.

| officers       |          | students       |          |
| -------------- | -------- | -------------- | -------- |
| officer_id     | officer_name | student_id   | student_name | course_name |
| 1              | John Doe   | 1            | Alice       | Math        |
| 2              | Jane Smith | 2            | Bob         | English     |

Execute the following query:

```sql
SELECT officers.officer_name, officers.address, students.course_name
FROM officers
LEFT JOIN students
ON officers.officer_id = students.student_id;
```

**Output:**

| officer_name | address   | course_name |
| ------------ | --------- | ----------- |
| John Doe     | [address] | Math        |
| Jane Smith   | [address] | English     |

## MySQL Right Outer Join

The MySQL Right Outer Join returns all rows from the RIGHT-hand table specified in the ON condition and only those rows from the other table where the join condition is fulfilled.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT [OUTER] JOIN table2
ON table1.column = table2.column;
```

**Image representation:**

![image](https://github.com/vansh-seth/MySQL/assets/111755254/128b8abd-4a1b-4c58-b68a-d5d4eb54d53a)

**Example:**

Consider two tables "officers" and "students", having the following data.

| officers       |          | students       |          |
| -------------- | -------- | -------------- | -------- |
| officer_id     | officer_name | student_id   | student_name | course_name |
| 1              | John Doe   | 1            | Alice       | Math        |
| 2              | Jane Smith | 2            | Bob         | English     |

Execute the following query:

```sql
SELECT officers.officer_name, officers.address, students.course_name, students.student_name
FROM officers
RIGHT JOIN students
ON officers.officer_id = students.student_id;
```

**Output:**

| officer_name | address   | course_name | student_name |
| ------------ | --------- | ----------- | ------------ |
| John Doe     | [address] | Math        | Alice        |
| [Null]       | [Null]    | English     | Bob          |


## MySQL Inner Join

The MySQL Inner Join is used to return only those results from the tables that match the specified condition and hide other rows and columns. MySQL assumes it as a default Join, so it is optional to use the Inner Join keyword with the query.

We can understand it with the following visual representation where Inner Joins return only the matching results from table1 and table2:

**MySQL Inner Join**

| table1  |          | table2  |          | Inner Join Result |
| ------- | -------- | ------- | -------- | ----------------- |
| col1    | col2     | col1    | col3     | col1, col2, col3  |
| A       | 1        | A       | x        | A, 1, x            |
| B       | 2        | C       | y        |                 |
| C       | 3        | D       | z        |                 |

**MySQL Inner Join Syntax:**

The Inner Join keyword is used with the SELECT statement and must be written after the FROM clause. The following syntax explains it more clearly:

```sql
SELECT columns
FROM table1
INNER JOIN table2 ON condition1
INNER JOIN table3 ON condition2
...;
```

In this syntax, we first have to select the column list, then specify the table name that will be joined to the main table, appears in the Inner Join (table1, table2), and finally, provide the condition after the ON keyword. The Join condition returns the matching rows between the tables specified in the Inner clause.

**MySQL Inner Join Example:**

Let us first create two tables "students" and "technologies" that contain the following data:

*Table: students*

| student_id | stud_fname | stud_lname | city     |
| ---------- | ---------- | ---------- | -------- |
| 1          | John       | Doe        | New York |
| 2          | Jane       | Smith      | Boston   |

*Table: technologies*

| tech_id | inst_name       | technology |
| ------- | --------------- | ---------- |
| 1       | Tech Institute  | Java       |
| 2       | Code Academy    | Python     |

To select records from both tables, execute the following query:

```sql
SELECT students.stud_fname, students.stud_lname, students.city, technologies.technology
FROM students
INNER JOIN technologies
ON students.student_id = technologies.tech_id;
```

After the successful execution of the query, it will give the following output:

| stud_fname | stud_lname | city     | technology |
| ---------- | ---------- | -------- | ---------- |
| John       | Doe        | New York | Java       |
| Jane       | Smith      | Boston   | Python     |

**MySQL Inner Join with Group By Clause:**

The Inner Join can also be used with the GROUP BY clause. The following statement returns student id, technology name, city, and institute name using the Inner Join clause with the GROUP BY clause.

```sql
SELECT students.student_id, technologies.inst_name, students.city, technologies.technology
FROM students
INNER JOIN technologies
ON students.student_id = technologies.tech_id
GROUP BY inst_name;
```

The above statement will give the following output:

| student_id | inst_name        | city     | technology |
| ---------- | ---------------  | -------- | ---------- |
| 1          | Tech Institute   | New York | Java       |
| 2          | Code Academy     | Boston   | Python     |

**MySQL Inner Join with USING Clause:**

Sometimes, the name of the columns is the same in both tables. In that case, we can use a USING keyword to access the records. The following query explains it more clearly:

```sql
SELECT student_id, inst_name, city, technology
FROM students
INNER JOIN technologies
USING (student_id);
```

It will give the following output:

| student_id | inst_name       | city     | technology |
| ---------- | --------------- | -------- | ---------- |
| 1          | Tech Institute  | New York | Java       |
| 2          | Code Academy    | Boston   | Python     |

**Inner Join with WHERE Clause:**

The WHERE clause enables you to return the filtered result. The following example illustrates this clause with Inner Join:

```sql
SELECT tech_id, inst_name, city, technology
FROM students
INNER JOIN technologies
USING (student_id) WHERE technology = "Java";
```

This statement gives the below result:

| tech_id | inst_name        | city     | technology |
| ------- | ---------------  | -------- | ---------- |
| 1       | Tech Institute   | New York | Java       |

**MySQL Inner Join Multiple Tables:**

We have already created two tables named students and technologies. Let us create one more table and name it as a contact.

*Table: contact*

| student_id | cellphone   |
| ---------- | ----------- |
| 1          | 123-456-7890 |
| 2          | 987-654-3210 |

Execute the following statement to join the three tables students, technologies, and contact:

```sql
SELECT student_id, inst_name, city, technology, cellphone
FROM students
INNER JOIN technologies USING (student_id)
INNER JOIN contact ORDER BY student_id;
```

After the successful execution of the above query, it will give the following output:

| student_id | inst_name        | city     | technology | cellphone   |
| ---------- | ---------------  | -------- | ---------- | ----------- |
| 1          | Tech Institute   | New York | Java       | 123-456-7890 |
| 2          | Code Academy     | Boston   | Python     | 987-654-3210 |

**MySQL Inner Join using Operators:**

MySQL allows many operators that can be used with Inner Join, such as greater than (>), less than (<), equal (=), not equal (=), etc. The following query returns the result whose income is in the range of 20000 to 80000:

```sql
SELECT emp_id, designation, income, qualification
FROM employee
INNER JOIN customer
WHERE income > 20000 and income < 80000;
```

This will give the following output:

| emp_id | designation | income | qualification |
| ------ | ------------ | ------ | -------------- |
| 1      | Manager      | 50000  | Graduate       |
| 3      | Analyst      | 60000  | Post Graduate  |

**MySQL Inner Join**

| emp_id | emp_name     | customer_id | customer_name | income |
| ------ | ------------ | ------------ | ------------- | ------ |
| 1      | John Doe      | 101          | Alice         | 50000  |
| 2      | Jane Smith    | 102          | Bob           | 70000  |
| 3      | Mike Johnson  | 103          | Charlie       | 60000  |
