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


