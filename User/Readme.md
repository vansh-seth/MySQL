## MySQL Create User

The MySQL Create User statement allows you to create a new user account in the MySQL server, providing authentication, SSL/TLS, resource-limit, role, and password management properties. This user is a record in the USER table, containing login information, account privileges, and host information for MySQL accounts. It is essential for accessing and managing databases.

### Syntax

```sql
CREATE USER [IF NOT EXISTS] account_name IDENTIFIED BY 'password';
```

The `account_name` consists of a username and hostname separated by '@' (e.g., `username@hostname`). If no hostname is provided, the user can connect from any host (`username@%`). The `IF NOT EXISTS` clause avoids errors when creating an existing user, providing a warning instead.

### Example

1. Open the MySQL server using the `mysql` client tool.

2. Enter the password for the account.

   ```bash
   Enter Password: ********
   ```

3. Execute the following command to display all users.

   ```sql
   mysql> SELECT user FROM mysql.user;
   ```

   Output:
   ```
   MySQL Create User
   ```

4. Create a new user.

   ```sql
   mysql> CREATE USER vansh@localhost IDENTIFIED BY '123';
   ```

   Verify the user creation:

   ```sql
   mysql> SELECT user FROM mysql.user;
   ```

   Output:
   ```
   MySQL Create User
   vansh
   ```

5. Use the `IF NOT EXISTS` clause.

   ```sql
   mysql> CREATE USER IF NOT EXISTS seth@localhost IDENTIFIED BY '123';
   ```

### Grant Privileges

Grant privileges to a new user using the `GRANT` statement. 

ALL PRIVILEGES: It permits all privileges to a new user account.
CREATE: It enables the user account to create databases and tables.
DROP: It enables the user account to drop databases and tables.
DELETE: It enables the user account to delete rows from a specific table.
INSERT: It enables the user account to insert rows into a specific table.
SELECT: It enables the user account to read a database.
UPDATE: It enables the user account to update table rows.
If you want to give all privileges to a newly created user, execute the following command.

Examples:

- Grant all privileges:

  ```sql
  mysql> GRANT ALL PRIVILEGES ON * . * TO vansh@localhost;
  ```

- Grant specific privileges:

  ```sql
  mysql> GRANT CREATE, SELECT, INSERT ON * . * TO vansh@localhost;
  ```

Flush privileges for changes to take effect immediately:

```sql
mysql> FLUSH PRIVILEGES;
```

Check existing privileges for a user:

```sql
mysql> SHOW GRANTS FOR username;
```

Make sure to replace `username` with the actual username you want to check.
