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
