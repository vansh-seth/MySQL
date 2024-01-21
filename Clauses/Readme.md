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
```

