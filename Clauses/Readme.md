# MySQL Clause
## MySQL WHERE Clause

The MySQL WHERE Clause is used with the SELECT, INSERT, UPDATE, and DELETE clauses to filter the results. It specifies a specific condition that must be met for the operation to take place.

## Syntax:

```sql
WHERE conditions;
```

### Parameter:

- `conditions`: Specifies the conditions that must be fulfilled for records to be selected.

## MySQL WHERE Clause with Single Condition

Let's consider an example of retrieving data from a table named "officers."

### Table Structure:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 1          | John Doe     | Mau     |
| 2          | Jane Doe     | Lucknow |
| 3          | Bob Smith    | Mau     |
| 4          | Alice Brown  | Lucknow |
| 5          | Charlie Lee  | Delhi   |

### Execute this query:

```sql
SELECT *  
FROM officers  
WHERE address = 'Mau';
```

#### Output:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 1          | John Doe     | Mau     |
| 3          | Bob Smith    | Mau     |

## MySQL WHERE Clause with AND Condition

In this example, we are retrieving data from the "officers" table with an AND condition.

### Execute the following query:

```sql
SELECT *  
FROM officers  
WHERE address = 'Lucknow'  
AND officer_id < 5;
```

#### Output:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 2          | Jane Doe     | Lucknow |

## MySQL WHERE Clause with OR Condition

Execute the following query to retrieve data with an OR condition:

```sql
SELECT *  
FROM officers  
WHERE address = 'Lucknow'  
OR address = 'Mau';
```

#### Output:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 1          | John Doe     | Mau     |
| 2          | Jane Doe     | Lucknow |
| 3          | Bob Smith    | Mau     |
| 4          | Alice Brown  | Lucknow |

## MySQL WHERE Clause with a Combination of AND & OR Conditions

You can use both AND and OR conditions in combination with the WHERE clause. See this example:

### Execute the following query:

```sql
SELECT *  
FROM officers  
WHERE (address = 'Mau' AND officer_name = 'Ajeet')  
OR (officer_id < 5);
```

#### Output:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 1          | John Doe     | Mau     |
| 3          | Bob Smith    | Mau     |
| 4          | Alice Brown  | Lucknow |


## MySQL DISTINCT Clause

The MySQL DISTINCT clause is used to remove duplicate records from the table and fetch only the unique records. The DISTINCT clause is only used with the SELECT statement.

## Syntax:

```sql
SELECT DISTINCT expressions  
FROM tables  
[WHERE conditions];
```

### Parameters:

- `expressions`: Specify the columns or calculations that you want to retrieve.
- `tables`: Specify the name of the tables from where you retrieve records. There must be at least one table listed in the FROM clause.
- `WHERE conditions`: It is optional. It specifies the conditions that must be met for the records to be selected.

**Note:**

- If you put only one expression in the DISTINCT clause, the query will return the unique values for that expression.
- If you put more than one expression in the DISTINCT clause, the query will retrieve unique combinations for the expressions listed.
- In MySQL, the DISTINCT clause doesn't ignore NULL values. So if you are using the DISTINCT clause in your SQL statement, your result set will include NULL as a distinct value.

## MySQL DISTINCT Clause with Single Expression

If you use a single expression, then the MySQL DISTINCT clause will return a single field with unique records (no duplicate record).

### Example:

#### Table:

| officer_id | officer_name | address |
|------------|--------------|---------|
| 1          | John Doe     | Mau     |
| 2          | Jane Doe     | Lucknow |
| 3          | Bob Smith    | Mau     |
| 4          | Alice Brown  | Lucknow |
| 5          | Charlie Lee  | Delhi   |

#### Query:

```sql
SELECT DISTINCT address  
FROM officers;
```

#### Output:

| address |
|---------|
| Mau     |
| Lucknow |
| Delhi   |

## MySQL DISTINCT Clause with Multiple Expressions

If you use multiple expressions with the DISTINCT Clause, then MySQL DISTINCT clause will remove duplicates from more than one field in your SELECT statement.

### Example:

#### Query:

```sql
SELECT DISTINCT officer_name, address  
FROM officers;
```

#### Output:

| officer_name | address |
|--------------|---------|
| John Doe     | Mau     |
| Jane Doe     | Lucknow |
| Bob Smith    | Mau     |
| Alice Brown  | Lucknow |
| Charlie Lee  | Delhi   |


