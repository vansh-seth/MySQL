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

