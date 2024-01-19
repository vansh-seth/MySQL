## MySQL Create Database

In MySQL, you can create a new database using the `CREATE DATABASE` statement. Below is the syntax and an example of creating a database.

### Syntax

```sql
CREATE DATABASE [IF NOT EXISTS] database_name
  [CHARACTER SET charset_name]
  [COLLATE collation_name];
```

- `database_name`: The name of the new database. It should be unique within the MySQL server instance. The `IF NOT EXISTS` clause prevents an error if the database already exists.
- `CHARACTER SET charset_name`: Optional. It specifies the character set to store every character in a string. If not provided, MySQL uses the default character set.
- `COLLATE collation_name`: Optional. It specifies how characters in a particular character set should be compared.

### Example

Let's create a database named "employeesdb" as an example:

```sql
mysql> CREATE DATABASE IF NOT EXISTS employeesdb;
```

This statement creates a new database named "employeesdb" if it doesn't already exist.

To review the details of the created database, you can use the following query:

```sql
mysql> SHOW CREATE DATABASE employeesdb;
```

This will show the database name, character set, and collation of the "employeesdb" database.

To check all the created databases on the server, you can use the following query:

```sql
mysql> SHOW DATABASES;
```

Finally, you can switch to the newly created database using the `USE` command:

```sql
mysql> USE employeesdb;
```

Now, you are ready to create tables and perform other operations within the "employeesdb" database.


## MySQL SELECT Database

In MySQL, you can use the `USE` command to select a specific database to work with. This is useful when there are multiple databases available on the MySQL server.

### Syntax

```sql
USE database_name;
```

### Example

Let's take an example of using a database named "customers":

```sql
USE customers;
```

This statement selects the "customers" database, allowing subsequent SQL commands to operate within that specific database context.

## MySQL Show/List Databases

In MySQL, you can use the `SHOW DATABASES` command to list all the databases available on the MySQL server host. Additionally, you can use pattern matching to filter the returned databases using the `LIKE` and `WHERE` clauses.

### List All Databases

To list all databases:

```sql
SHOW DATABASES;
```

This command will display a list of all databases on the MySQL server.

### Pattern Matching with LIKE Clause

To list databases that match a specific pattern:

```sql
SHOW DATABASES LIKE 'pattern';
```

Replace 'pattern' with the desired pattern. For example:

```sql
SHOW DATABASES LIKE 's%';
```

This will display databases whose names start with 's'.

### Using WHERE Clause

You can also use the `WHERE` clause for more complex filtering:

```sql
SELECT schema_name FROM information_schema.schemata WHERE schema_name LIKE 's%';
```

This statement achieves the same result as the previous example but uses the `SELECT` statement on the `information_schema.schemata` table.

Remember that the `%` sign in pattern matching represents zero, one, or multiple characters.

**Note**: The `SHOW SCHEMAS` statement is a synonym for `SHOW DATABASES`, and both can be used interchangeably.

## MySQL DROP Database

In MySQL, you can drop (delete) an existing database using the `DROP DATABASE` statement. Alternatively, you can use `DROP SCHEMA`, as the terms "schema" and "database" are interchangeable in MySQL.

### Syntax

```sql
DROP DATABASE [IF EXISTS] database_name;
```

or

```sql
DROP SCHEMA [IF EXISTS] database_name;
```

- `database_name`: The name of the existing database you want to delete. It should be unique within the MySQL server instance.
- `IF EXISTS`: Optional. Used to prevent an error if the database does not exist.

### Example

Let's assume we want to drop a database named "mytestdb_copy". Here's how you can do it:

1. Open the MySQL console and enter your password if required.

2. Use the following command to see all available databases on the server:

   ```sql
   SHOW DATABASES;
   ```

   This will display a list of databases.

3. To drop the "mytestdb_copy" database, execute the following statement:

   ```sql
   DROP DATABASE mytestdb_copy;
   ```

   or

   ```sql
   DROP SCHEMA mytestdb_copy;
   ```

4. To verify that the database has been dropped, you can again execute the `SHOW DATABASES` command, and you should not see "mytestdb_copy" in the list.

   ```sql
   SHOW DATABASES;
   ```

   The output should confirm that the database has been removed.

**Note:** Be cautious when using `DROP DATABASE` as it permanently deletes the database and its contents. Ensure you have a backup if needed. The `IF EXISTS` clause prevents an error if the database doesn't exist.

