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



## MySQL Drop User

The MySQL `DROP USER` statement allows you to remove one or more user accounts and their privileges from the database server. If the account does not exist, it results in an error. To use this statement, you need the global privilege of `CREATE USER` or the `DELETE` privilege for the MySQL system schema.

### Syntax

```sql
DROP USER 'account_name';
```

The `account_name` is specified as `username@hostname`, where the username is the account's name, and hostname is the server name of the user account.

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
   acc
   root
   seth
   vansh
   ```

4. To drop a user account, execute the following statement.

   ```sql
   DROP USER vansh@localhost;
   ```

   After execution, check the users again:

   ```sql
   mysql> SELECT user FROM mysql.user;
   ```

   Output:
   ```
   acc
   root
   seth
   ```

   The username 'vansh' is no longer present.

5. To drop multiple user accounts, use the following command.

   ```sql
   DROP USER seth@localhost, acc@localhost;
   ```

   After execution, check the users again:

   ```sql
   mysql> SELECT user FROM mysql.user;
   ```

   Output:
   ```
   root
   ```

   The usernames 'seth' and 'acc' are no longer present.

**Note:** The `DROP USER` statement cannot automatically close any open user sessions. If the session of the dropped account is active, the statement takes effect only when the session is closed. The user account is dropped only when the session is closed, and the user's next attempt to log in will be unsuccessful.



## MySQL Show Users / List All Users

In MySQL, there isn't a specific `SHOW USERS` command like `SHOW DATABASES` or `SHOW TABLES` to display a list of all users. However, you can use a query to retrieve information from the `mysql.user` table. Here's an example:

```sql
mysql> SELECT user FROM mysql.user;
```

This query retrieves the `user` column from the `mysql.user` table, displaying the list of all users in the MySQL server.

### Example Usage

1. Open the MySQL server using the `mysql` client tool and log in as an administrator.

   ```bash
   mysql -u root -p
   ```

   Enter your password when prompted.

2. Use the `mysql` database.

   ```sql
   mysql> use mysql;
   ```

3. Execute the query to display all users.

   ```sql
   mysql> SELECT user FROM user;
   ```

   This will show the list of users in your local database.

### Additional Information

To get more details about the `mysql.user` table, you can use the `DESC` command:

```sql
mysql> DESC user;
```

This command will list all available columns in the `mysql.user` table.

For specific information like hostname, password expiration status, and account locking, you can execute a query like:

```sql
mysql> SELECT user, host, account_locked, password_expired FROM user;
```

To show the current user, you can use either the `user()` or `current_user()` function:

```sql
mysql> SELECT user();
-- or,
mysql> SELECT current_user();
```

To display the currently logged users in the database server, you can use the following query:

```sql
mysql> SELECT user, host, db, command FROM information_schema.processlist;
```

This command provides information about the users currently logged into the database server.


## Change MySQL User Password

Changing the password for a MySQL user account can be accomplished using different statements. Here are three ways to change a user password:

### 1. Using UPDATE Statement

```sql
USE mysql;

UPDATE user SET authentication_string = PASSWORD('123') WHERE user = 'vansh' AND host = 'localhost';

FLUSH PRIVILEGES;
```

### 2. Using SET PASSWORD Statement


```sql
SET PASSWORD FOR 'vansh'@'localhost' = '123';
```

### 3. Using ALTER USER Statement

```sql
ALTER USER vansh@localhost IDENTIFIED BY '1234';
```

### Resetting MySQL Root Account Password

To reset the MySQL root account password, you can force a stop and restart of the MySQL database server without using the grant table validation. This is an alternative method in case you need to reset the root password:

1. Stop the MySQL server.

2. Start the MySQL server with the `--skip-grant-tables` option:

    ```bash
    mysqld --skip-grant-tables &
    ```

3. Connect to the MySQL server without a password:

    ```bash
    mysql -u root
    ```

4. Update the root password:

    ```sql
    FLUSH PRIVILEGES;
    ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
    ```

5. Stop the MySQL server.

6. Start the MySQL server normally.

Please replace 'new_password' with the desired new password for the root user. This process allows you to reset the root password without using the grant table validation.
