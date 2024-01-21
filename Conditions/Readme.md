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


