# MySQL Data Types

A **Data Type** specifies a particular type of data, like integer, floating points, Boolean, etc. It also identifies the possible values for that type, the operations that can be performed on that type, and the way the values of that type are stored. In MySQL, each database table has many columns and contains specific data types for each column.

We can determine the data type in MySQL with the following characteristics:

- The type of values (fixed or variable) it represents.
- The storage space it takes is based on whether the values are a fixed-length or variable length.
- Its values can be indexed or not.
- How MySQL performs a comparison of values of a particular data type.

MySQL supports a lot of SQL standard data types in various categories. It uses many different data types that can be broken into the following categories: numeric, date and time, string types, spatial types, and JSON data types.

## Numeric Data Type

MySQL has all essential SQL numeric data types, including exact and approximate numeric data types. It also supports the BIT datatype to store bit values. In MySQL, numeric data types are categorized into two types, either signed or unsigned, except for the bit data type.

The following table contains all numeric data types that are supported in MySQL:

| Data Type     | Description                                             |
| ------------- | ------------------------------------------------------- |
| TINYINT       | A very small integer that can be signed or unsigned. range is from -128 to 127    |
| SMALLINT      | A small integer that can be signed or unsigned. range is from -32768 to 32767         |
| MEDIUMINT     | A medium-sized integer that can be signed or unsigned. range is from -8388608 to 8388607.  |
| INT           | A normal-sized integer that can be signed or unsigned. range is from -2147483648 to 2147483647 |
| BIGINT        | A large integer that can be signed or unsigned. range is from -9223372036854775808 to 9223372036854775807         |
| FLOAT(m,d)    | It is a floating-point number that cannot be unsigned. You can define the display length (m) and the number of decimals (d). This is not required and will default to 10,2, where 2 is the number of decimals, and 10 is the total number of digits (including decimals). Decimal precision can go to 24 places for a float type. It requires 2 bytes for storage. |
| DECIMAL(m,d)  | An unpacked floating-point number that cannot be unsigned. In unpacked decimals, each decimal corresponds to one byte. Defining the display length (m) and the number of decimals (d) is required. Numeric is a synonym for decimal.  |
| DOUBLE(m,d)   | It is a double-precision floating-point number that cannot be unsigned. You can define the display length (m) and the number of decimals (d). This is not required and will default to 16,4, where 4 is the number of decimals. Decimal precision can go to 53 places for a double. Real is a synonym for double. It requires 8 bytes for storage. |
| BIT(m)        | Used for storing bit values into the table column. range of 1 to 64.       |
| BOOL          | Used only for the true and false condition.              |
| BOOLEAN       | Similar to BOOL.                                        |

## Date and Time Data Type

This data type is used to represent temporal values such as date, time, datetime, timestamp, and year. Each temporal type contains values, including zero. When we insert the invalid value, MySQL cannot represent it, and then zero value is used.

The following table illustrates all date and time data types that are supported in MySQL:

| Data Type        | Maximum Size                 | Explanation                                              |
| ---------------- | ---------------------------- | -------------------------------------------------------- |
| YEAR[(2|4)]      | Year value as 2 digits or 4 digits| Default is 4 digits. It takes 1 byte for storage. |
| DATE             | Values range from '1000-01-01' to '9999-12-31'| Displayed as 'yyyy-mm-dd'. It takes 3 bytes for storage. |
| TIME             | Values range from '-838:59:59' to '838:59:59'| Displayed as 'HH:MM:SS'. It takes 3 bytes plus fractional seconds for storage. |
| DATETIME         | Values range from '1000-01-01 00:00:00' to '9999-12-31 23:59:59'| Displayed as 'yyyy-mm-dd hh:mm:ss'. It takes 5 bytes plus fractional seconds for storage. |
| TIMESTAMP(m)     | Values range from '1970-01-01 00:00:01' UTC to '2038-01-19 03:14:07' TC| Displayed as 'YYYY-MM-DD HH:MM:SS'. It takes 4 bytes plus fractional seconds for storage. |

## String Data Types

The string data type is used to hold plain text and binary data, such as files, images, etc. MySQL can perform searching and comparison of string values based on pattern matching, such as LIKE operator, Regular Expressions, etc.

The following table illustrates all string data types that are supported in MySQL:

| Data Type       | Maximum Size                  | Explanation                                              |
| --------------- | ----------------------------- | -------------------------------------------------------- |
| CHAR(size)      | Maximum size of 255 characters. | Fixed-length strings. Space padded on the right to equal size characters. |
| VARCHAR(size)   | Maximum size of 255 characters. | Variable-length string.                                   |
| TINYTEXT(size)  | Maximum size of 255 characters. | Size is the number of characters to store.|                                                           
| TEXT(size)      | Maximum size of 65,535 characters. | Size is the number of characters to store.|
| MEDIUMTEXT(size)| Maximum size of 16,777,215 characters. | Size is the number of characters to store.                                                     |
| LONGTEXT(size)  | Maximum size of 4GB or 4,294,967,295 characters. | size is the number of characters to store.                                            |
| BINARY(size)    | It can have a maximum size of 255 characters | Maximum size of 255 characters. | size is the number of binary characters to store. Fixed-length strings. Space padded on the right to equal size characters. |
| VARBINARY(size) | It can have a maximum size of 255 characters. | Maximum size of 255 characters. | Variable-length string.                                   |
| ENUM            | Takes 1 or 2 bytes depending on the number of enumeration values. Maximum of 65,535 values. | Short for enumeration, each column may have one of the specified possible values. Uses numeric indexes (1, 2, 3…) to represent string values. |
| SET             | Takes 1, 2, 3, 4, or 8 bytes depending on the number of set members. Maximum of 64 members. | Can hold zero or more, or any number of string values. Must be chosen from a predefined list of values specified during table creation. |

## Binary Large Object Data Types (BLOB)

BLOB in MySQL is a data type that can hold a variable amount of data. They are categorized into four different types based on the maximum length of values they can hold.

The following table shows all Binary Large Object data types that are supported in MySQL:

| Data Type       | Maximum Size                  |
| --------------- | ----------------------------- |
| TINYBLOB        | Maximum size of 255 bytes.    |
| BLOB(size)      | Maximum size of 65,535 bytes.  |
| MEDIUMBLOB      | Maximum size of 16,777,215 bytes. |
| LONGBLOB        | Maximum size of 4gb or 4,294,967,295 bytes. |
