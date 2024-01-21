# MySQL Condition
# MySQL AND Condition

The MySQL AND condition is used with SELECT, INSERT, UPDATE, or DELETE statements to test two or more conditions in an individual query.

## Syntax:

```sql
WHERE condition1  
AND condition2  
...  
AND condition_n;
```

### Parameter Explanation:

- `condition1, condition2, ... condition_n`: Specifies all conditions that must be fulfilled for the records to be selected.

## MySQL AND Example

The following example specifies how to use the AND condition in MySQL with the SELECT statement.

Consider a table "cus_tbl", having the following data:

#### Table: cus_tbl

| cus_id | cus_firstname | cus_lastname | cus_age |
|--------|---------------|--------------|---------|
| 1      | John          | Doe          | 25      |
| 2      | Jane          | Smith        | 30      |
| 3      | Bob           | Brown        | 22      |
| 4      | Ajeet         | Kumar        | 28      |
| 5      | Charlie       | Lee          | 35      |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM cus_tbl  
WHERE cus_firstname = 'Ajeet'  
AND cus_id > 3;
```

#### Output:

| cus_id | cus_firstname | cus_lastname | cus_age |
|--------|---------------|--------------|---------|
| 4      | Ajeet         | Kumar        | 28      |
| 5      | Charlie       | Lee          | 35      |

## MySQL OR Condition

The MySQL OR condition specifies that if you take two or more conditions then one of the conditions must be fulfilled to get the records as a result.

## Syntax:

```sql
WHERE condition1  
OR condition2  
...  
OR condition_n;
```

### Parameter Explanation:

- `condition1, condition2, ... condition_n`: Specifies all conditions that must be fulfilled for the records to be selected.

## MySQL OR Example

The following example specifies how to use the OR condition in MySQL with the SELECT statement.

Consider a table "cus_tbl", having the following data:

#### Table: cus_tbl

| cus_id | cus_firstname | cus_lastname | cus_age |
|--------|---------------|--------------|---------|
| 1      | John          | Doe          | 25      |
| 2      | Jane          | Smith        | 30      |
| 3      | Bob           | Brown        | 22      |
| 4      | Ajeet         | Kumar        | 28      |
| 5      | Charlie       | Lee          | 35      |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM cus_tbl  
WHERE cus_firstname = 'Ajeet'  
OR cus_id > 100;
```

#### Output:

| cus_id | cus_firstname | cus_lastname | cus_age |
|--------|---------------|--------------|---------|
| 4      | Ajeet         | Kumar        | 28      |

**Note:** In the above example, you can see that the second condition "cus_id" is incorrect, but the query is displaying the correct result because of the OR condition.

## MySQL AND & OR Conditions

In MySQL, you can use AND & OR conditions together with the SELECT, INSERT, UPDATE, and DELETE statements. When combining these conditions, you must be aware of where to use round brackets so that the database knows the order to evaluate each condition.

## Syntax:

```sql
WHERE condition1  
AND condition2  
...  
OR condition_n;
```

### Parameter:

- `condition1, condition2, ... condition_n`: Specifies the conditions that are evaluated to determine if the records will be selected.

## MySQL AND OR Example

Consider a table "students", having the following data.

#### Table: students

| student_id | student_name | course_name |
|------------|--------------|-------------|
| 1          | Aryan        | Java        |
| 2          | Bob          | Python      |
| 3          | Charlie      | Java        |
| 4          | David        | C++         |
| 5          | Emily        | Python      |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM students  
WHERE (course_name = 'Java' AND student_name = 'Aryan')  
OR (student_id < 2);
```

#### Output:

| student_id | student_name | course_name |
|------------|--------------|-------------|
| 1          | Aryan        | Java        |


## MySQL LIKE Condition

In MySQL, the LIKE condition is used to perform pattern matching to find the correct result. It is used in SELECT, INSERT, UPDATE, and DELETE statements with the combination of the WHERE clause.

## Syntax:

```sql
expression LIKE pattern [ ESCAPE 'escape_character' ]
```

### Parameters:

- `expression`: It specifies a column or field.
- `pattern`: It is a character expression that contains pattern matching.
- `escape_character`: It is optional. It allows you to test for literal instances of a wildcard character such as % or _. If you do not provide the escape_character, MySQL assumes that "\" is the escape_character.

## MySQL LIKE Examples

1) **Using % (percent) Wildcard:**

Consider a table "officers" having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | John Doe     | Mau       |
| 2          | Jane Doe     | Lucknow   |
| 3          | Bob Smith    | Mau       |
| 4          | Alice Brown  | Lucknow   |
| 5          | Charlie Lee  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT officer_name  
FROM officers  
WHERE address LIKE 'Luck%';
```

#### Output:

| officer_name |
|--------------|
| Jane Doe     |
| Alice Brown  |

2) **Using _ (Underscore) Wildcard:**

We are using the same table "officers" in this example too.

Execute the following query:

#### Query:

```sql
SELECT officer_name  
FROM officers  
WHERE address LIKE 'Luc_now';
```

#### Output:

| officer_name |
|--------------|
| Jane Doe     |

3) **Using NOT Operator:**

You can also use the NOT operator with MySQL LIKE condition. This example shows the use of % wildcard with the NOT Operator.

Consider a table "officers" having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | John Doe     | Mau       |
| 2          | Jane Doe     | Lucknow   |
| 3          | Bob Smith    | Mau       |
| 4          | Alice Brown  | Lucknow   |
| 5          | Charlie Lee  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT officer_name  
FROM officers  
WHERE address NOT LIKE 'Luck%';
```

#### Output:

| officer_name |
|--------------|
| John Doe     |
| Bob Smith    |
| Charlie Lee  |

**Note:*** In the above example, you can see that the addresses NOT LIKE 'Luck%' are only shown.

## MySQL IN Condition

The MySQL IN condition is used to reduce the use of multiple OR conditions in a SELECT, INSERT, UPDATE, and DELETE statement.

## Syntax:

```sql
expression IN (value1, value2, .... value_n);
```

### Parameters:

- `expression`: It specifies a value to test.
- `value1, value2, ... or value_n`: These are the values to test against the expression. If any of these values match the expression, then the IN condition will evaluate to true. This is a quick method to test if any one of the values matches the expression.

## MySQL IN Example

Consider a table "officers", having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name IN ('Ajeet', 'Vimal', 'Deepika');
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |

Let's see why it is preferred over OR condition:

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name = 'Ajeet'  
OR officer_name = 'Vimal'  
OR officer_name = 'Deepika';
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |

It also produces the same result. So, the IN condition is preferred over the OR condition because it has a minimum number of codes.


## MySQL NOT Condition

The MySQL NOT condition is opposite of MySQL IN condition. It is used to negate a condition in a SELECT, INSERT, UPDATE, or DELETE statement.

## Syntax:

```sql
NOT condition
```

### Parameter:

- `condition`: It specifies the conditions that you want to negate.

## MySQL NOT Operator Examples

### Using NOT Operator with IN condition

Consider a table "officers", having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name NOT IN ('Ajeet', 'Vimal', 'Deepika');
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

### Using NOT Operator with IS NULL condition

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name IS NOT NULL;
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

### Using NOT Operator with LIKE condition

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name NOT LIKE 'A%';
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 2          | Vimal        | Lucknow   |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

### Using NOT Operator with BETWEEN condition

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_id NOT BETWEEN 3 AND 5;
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |


## MySQL IS NULL Condition

MySQL IS NULL condition is used to check if there is a NULL value in the expression. It is used with SELECT, INSERT, UPDATE, and DELETE statements.

## Syntax:

```sql
expression IS NULL
```

### Parameter:

- `expression`: It specifies a value to test if it is NULL value.

Consider a table "officers" having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name IS NULL;
```

#### Output:

Empty result set

**Note:** Here, you are getting the empty result because there is no NULL value in the `officer_name` column.


## MySQL IS NOT NULL Condition

MySQL IS NOT NULL condition is used to check the NOT NULL value in the expression. It is used with SELECT, INSERT, UPDATE, and DELETE statements.

## Syntax:

```sql
expression IS NOT NULL
```

### Parameter:

- `expression`: It specifies a value to test if it is not NULL value.

Consider a table "officers" having the following data.

#### Table: officers

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

Execute the following query:

#### Query:

```sql
SELECT *  
FROM officers  
WHERE officer_name IS NOT NULL;
```

#### Output:

| officer_id | officer_name | address   |
|------------|--------------|-----------|
| 1          | Ajeet        | Mau       |
| 2          | Vimal        | Lucknow   |
| 3          | Deepika      | Mau       |
| 4          | Bob Smith    | Lucknow   |
| 5          | Alice Brown  | Mau       |

**Note:** Here, you are getting the complete "officers" table as a result because every value is NOT NULL in the table.


