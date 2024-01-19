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
