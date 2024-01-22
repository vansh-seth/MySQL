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


