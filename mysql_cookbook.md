# Mysql CookBook

#### DQL

    SELECT *
    FROM table_name
    WHERE condition1 AND/OR condition2 AND/OR condition3...;

    SELECT *
    FROM table_name
    WHERE NOT (condition1 AND/OR condition2);

    SELECT *
    FROM table_name
    WHERE column_name NOT IN/IN (values1, values2...); 

    SELECT *
    FROM table_name
    WHERE column_name BETWEEN value1 AND value2;

    SELECT *
    FROM table_name
    WHERE column_name LIKE 'pattern';

    SELECT column1_name AS column1_alias, column2...,
    FROM table_name;

    SELECT CONCAT(column1, " ", column2) AS 'new_temp_column_name'
    FROM table_name;

    SELECT x.column1, x.column2, y.column1, y.column2
    FROM table_1 AS x, table_2 AS y
    WHERE x.column1 < 2 AND y.column1 > 5;

    SELECT table1_name.column_name
    FROM table1_name
    INNER JOIN table2_name
    ON table1_name.column_name = table2_name.column_name;

    SELECT table1_name.column_name
    FROM table1_name
    LEFT JOIN table2_name
    ON table1_name.column_name = table2_name.column_name;

    SELECT table1_name.column_name
    FROM table1_name
    RIGHT JOIN table2_name
    ON table1_name.column_name = table2_name.column_name;

    SELECT table1_name.column_name
    FROM table1_name
    OUTER JOIN table2_name
    ON table1_name.column_name = table2_name.column_name;

    SELECT column1, column2
    FROM table1
    UNION/ALL
    SELECT column1, column2
    FROM table2;

    SELECT column1, column2, MAX(column1)
    FROM table1
    WHERE condition2
    GROUP BY column1, column2;
    HAVING group_condition;

Subquery:

    SELECT column_name(s)
    FROM table_name
    WHERE ? <=  
    (SELECT column_name FROM table_name WHERE condition);

#### DML

    INSERT INTO table_name (column1, column2, column3)
    VALUES (column1_value, column2_value, column3_value);

    REPLACE INTO table_name (column1, column2, column3)
    VALUES (column1_value, column2_value, column3_value);

    REPLACE INTO table_name (column1, column2, column3)
    SET column_name = new_value, column_name1 = new_value...;

#### DDL

    CREATE TABLE Customers (
        CustomerID INT NOT NULL PRIMARY KEY,
        FullName VARCHAR(100) NOT NULL,
        PhoneNumber INT NOT NULL UNIQUE
    );

    CREATE TABLE Bookings (
        BookingID INT NOT NULL PRIMARY KEY,
        BookingDate DATE NOT NULL,
        TableNumber INT NOT NULL,
        NumberOfGuests INT NOT NULL CHECK(NumberOfGuests<=8),
        CustomerID INT NOT NULL,
        FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID) ON DELETE CASCADE ON UPDATE CASCADE
    );

    SHOW COLUMNS FROM Bookings;

    ALTER TABLE table_name  ADD/MODIFY/DROP column_name type constraints, MODIFY column_name2 type constraints,...;

Copy data and metadata local and accross databases:

    CREATE TABLE new_table_name
    SELECT columns...
    FROM existing_table_name;
    WHERE condition;

    CREATE TABLE database_X_name.new_table_name
    SELECT columns...
    FROM database_Y_name.existing_table_name;
    WHERE condition;

Copy with constraints and add data:

    CREATE TABLE new_table_name LIKE existing_table_name;
    INSERT INTO new_table_name SELECT * from existing_table_name;
    SHOW COLUMNS FROM new_table_name;
    SELECT * FROM new_table_name;

Create views:

    CREATE VIEW view_name AS
    SELECT column1, column2
    FROM table_name
    WHERE condition;

    RENAME TABLE old_table_name TO new_table_name;

    DROP view view_name;

#### Functions

AGGREGATE FUNCTIONS:

    SUM() AVG() MAX() MIN() COUNT()

MATH FUNCTIONS:

    ROUND() MOD()

STRING FUNCTIONS:

    CONCAT() SUBSTR() UCASE() LCASE()

DATE FUNCTIONS:

    CURRENT_DATE() CURRENT_TIME() DATE_FORMAT() DATEDIFF()

COMPARISON FUNCTIONS:

    GREATEST() LEAST() ISNULL()

CONTROLL FLOW FUNCTIONS:

    SELECT column_name
    CASE
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ELSE result
    END AS alias
    FROM table_name;

#### Stored Procedures

    CREATE PROCEDURE ProcedureName(parameter_value INT)
    SELECT column_name
    FROM table_name
    WHERE column_value = parameter_value;   

    CALL ProcedureName();

    DROP PROCEDURE ProcedureName;

#### User defined Functions

    
