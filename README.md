### SQL Basic Query

- To show all databases available on your system

```
SHOW DATABASES;
```

- To select a particular database

```
USE <databases name>;
```

- To list all the tables of a particular selected database

```
SHOW TABLES;
```

- To create a new database

```
CREATE DATABASE <name of db>
```

- To create a new table

```
CREATE TABLE <name of table> (
    <column name 1> [datatype],
    <column name 2> [datatype],
    .
    .
);
```

For example

```
CREATE TABLE studentsOfClass10(Name VARCHAR(25), FatherName VARCHAR(25), MotherName VARCHAR(25), Fee INTEGER);
```

- To Show structure and description of table

```
DESC <name of table>
```

- To insert value into table

```
INSERT INTO studentsOfClass10 (Name, FatherName, MotherName, Fees) VALUES ("Abc", "Cde", "Def", 3000);
```

- To get a specific column data from a table

```
SELECT <name of column> FROM <name of table>;
```

- Use `*` in place of <name of column> to get all the column details

```
SELECT * FROM <name of table>
```

- Create a table with some constraints

```
CREATE TABLE <name of table> (
    <column name 1> [datatype] [constraints],
    <column name 1> [datatype] [constraints],
    <column name 1> [datatype] [constraints],
    .
    .
);
```

For example

```
CREATE TABLE <table name> (Name VARCHAR(25) NOT NULL, Gender ENUM("Male", "Female", "Other"), Subject VARCHAR(250) DEFAULT "None");
```

- To insert multiple values into table

```
INSERT INTO studentsOfClass10 (Name, FatherName, MotherName, Fees) VALUES ("Abc", "Cde", "Def", 3000),("fgh", "hij", "jkl", 3000),...;
```

### WHERE clause

- Conditions -> comparison of column data with your values

```
SELECT * FROM <name of table> WHERE <condition>;
```

For example

```
SELECT * FROM teachersinfo WHERE subject = 'CS';
```

- Join two condition

Using AND

```
SELECT * FROM <name of table> WHERE <condition> AND <condition>;
```

Using OR

```
SELECT * FROM <name of table> WHERE <condition> OR <condition>;
```

Using NOT

```
SELECT * FROM <name of table> WHERE NOT <condition>;
```

For example

```
SELECT * FROM teachersinfo WHERE subject = 'None' AND Gender = 'Male';

SELECT * FROM teachersinfo WHERE Subject = 'None' OR Gender = 'Male';

SELECT * FROM teachersinfo WHERE NOT Subject = 'None';
```

---

### LIKE Operator

    Syntax

        SELECT * FROM <table name> WHERE <field name> LIKE '<condition>';

- Return all the names which end with the character `an`.

```
SELECT * FROM teachersinfo WHERE Name LIKE '%an';
```

- Return all the names containing the letter `a`.

```
SELECT * FROM teachersinfo WHERE Name LIKE '%a%';
```

- Return all the names where the column starts with any character, followed by `am`.

```
SELECT * FROM teachersinfo WHERE Name LIKE '_am%';
```

### Sort Data

- In ascending order

```
SELECT * FROM <table name> ORDER BY <field name>;
```

- In descending order

```
SELECT * FROM <table name> ORDER BY field name> DESC;
```

For example

```
SELECT * FROM teachersinfo ORDER BY NAME;

SELECT * FROM teachersinfo ORDER BY NAME DESC;
```

- Using LIMIT retrieve Top Three Records Sorted by Name in Descending Order

```
SELECT * FROM teachersinfo ORDER BY NAME DESC LIMIT 3;
```

### DELETE

- Delete First Record with `a` in <field name>

```
DELETE FROM <table name> WHERE <field name> LIKE "%a%" ORDER BY <field name> LIMIT 1;
```

- Delete all the data from table / Emptying Table: Simple Deletion

```
DELETE FROM <table name>;
```

### UPDATE

- Update table with new value based on condition.

```
UPDATE <table name> SET <key> = <value> WHERE <key> = <value>;
```

For example

```
UPDATE students SET Name = "ABC" WHERE Name = "AB";
```

#### ALTER

- Update table column and their properties.

```
ALTER TABLE <table name> CHANGE <old value> <new value> [add constraints];
```

For example

```
ALTER TABLE randomdata CHANGE Name FullName VARCHAR(30);
```

- Add new column in table

```
ALTER TABLE <table name> ADD <column name> <datatype> [constraints];
```

For example

```
ALTER TABLE randomdata ADD Salary DECIMAL(10,2) DEFAULT 0.00;
```

- Add a new column at a specific position.

```
ALTER TABLE <table name> ADD <column name> <datatype> AFTER <name of column>;
```

For example

```
ALTER TABLE randomdata ADD Role VARCHAR(20) AFTER FullName;
```

- Delete/Drop a column

```
ALTER TABLE <table name> DROP <column name>;
```

- Retrieve data info as Alias

```
SELECT <column name> AS "<alias name>" FROM <table name>;
```

- Retrieve two column info using CONCAT

```
SELECT CONCAT(<column name>, ' ', <column name>) AS "<alias name>" FROM <table name>;
```

- Count Records Meeting Condition

```
SELECT COUNT(*) AS "<alias name>" FROM <table name> WHERE <condition>;
```

### Aggregate Functions

#### Sum

- Summing values from a table

```
SELECT SUM(<column name>) FROM <table name>;
```

```
SELECT SUM(<column name>) FROM <table name> WHERE <condition>;
```

```
SELECT SUM(<column name>) AS "<alias name>" FROM <table name> WHERE <condition>;
```

#### Average/Min/Max

- Calculate Average Value from Table

```
SELECT AVG(<column name>) FROM <table name>;
```

You can do all the things you can do with Sum

### GROUP BY

Organizing Data for Analysis

- Count Records by Column Values

```
SELECT <column name>, COUNT(*) AS "<alias name>" FROM <table name> GROUP BY <column name>;
```

```
SELECT <column name>, AVG(<column name>) AS "<alias name>" FROM <table name> GROUP BY <column name>;
```

```
SELECT <column name>, MAX(<column name>) AS "<alias name>" FROM weather GROUP BY <column name>;
```

### JOIN

JOIN is a clause used to combine rows from two or more tables based on a related column between them. It allows you to retrieve data from multiple tables in a single query by specifying how the tables are related.

- INNER join

```
SELECT * FROM <table name> AS <alias> INNER JOIN <table name> AS <alias> ON <alias>.<column name> = <alias>.<column name>;
```

- LEFT join

```
SELECT * FROM <table name> AS <alias> LEFT JOIN <table name> AS <alias> ON <alias>.<column name> = <alias>.<column name>;
```

- RIGHT join

```
SELECT * FROM <table name> AS <alias> RIGHT JOIN <table name> AS <alias> ON <alias>.<column name> = <alias>.<column name>;
```

For example

```
SELECT * FROM airports AS a INNER JOIN cities AS c ON a.cityId = c.id;
```

- FULL OUTER join

MySQL does not support FULL OUTER JOIN directly. However, you can simulate a full outer join using a combination of LEFT JOIN, RIGHT JOIN, and UNION

```
SELECT * FROM <table name> AS <alias> LEFT JOIN <table name> AS <alias> ON <alias>.<column name> = <alias>.<column name> UNION SELECT * FROM <table name> AS <alias> RIGHT JOIN <table name> AS <alias> ON <alias>.<column name> = <alias>.<column name>;
```

For example

```
SELECT * FROM airports AS a LEFT JOIN cities AS c ON a.cityId = c.id UNION SELECT * FROM airports AS a RIGHT JOIN cities AS c ON a.cityId = c.id;
```

- NATURAL JOIN

```
SELECT * FROM table1 NATURAL JOIN table2;
```

### Database Schema

Database schema is blueprint of the actual db

### Functional Dependency

    column -> attribute
    row -> tuples

functional dependency define relationship between 2 attributes

For example

    X -> Y

    Y is functionally dependent on X
    means that, for every valid value of X we can uniquely identify Y.

For example

employee data

```
+--------------+--------------+-----------+
| Id           | Name         | Salary    |
+--------------+--------------+-----------+
| 1            | ABC          |      8000 |
| 2            | DEF          | 120000.00 |
+--------------+--------------+-----------+
```

e.Id -> e.Name ✔️ (e.Name is functionally dependent on e.Id)

e.Id -> e.Salary ✔️ (e.Salary is functionally dependent on e.Id)

But

e.name -> e.Salary ❌

Because two employees can have the same name

### DB keys

Keys are set of attributes that help us to uniquely identify a records in different situation

keys 
```
    Super
    Condidate
    Composite
    Primary
    Alternate
    Foreign
    Unique
```

- Super key

A super key is a set of one or more columns(attributes) that, taken collectively, uniquely identifies each row in a table

For example

```
    +--------+--------------+-----------+
    | e_Id   | e_Name       | e_phn     |
    +--------+--------------+-----------+
    | 1      | ABC          |      1234 |
    | 2      | DEF          |    909090 |
    +--------+--------------+-----------+

uniquely identifies
{
    e_Id
    (e_Id, e_Name)
    (e_Name, e_phn)
    .
    .
    ...
}

```

- Condidate key

Minimum set of attributes that can uniquely identify a records

```
    +--------+--------------+-----------+
    | e_Id   | e_Name       | e_phn     |
    +--------+--------------+-----------+
    | 1      | ABC          |      1234 |
    | 2      | DEF          |    909090 |
    | 3      | ABC          |    876543 |
    +--------+--------------+-----------+

Minimum uniquely identify
{
    e_Id
    e_phn
}

```

- Composite key
A composite key, also known as a compound key, is a key that consist of 2 or more than 2 attributes, that togather uniquely identify a record.
The attributes that form composite key are not any key independently.

```
    +------------+------------+------------+
    | StudentID  | CourseID   | Marks      |
    +------------+------------+------------+
    |    101     |    CSE101  |         90 |
    |    101     |    MAT102  |         78 |
    |    102     |    CSE101  |         45 |
    |    103     |    PHY103  |         90 |
    |    104     |    CSE101  |         45 |
    |    104     |    MAT102  |         63 |
    +------------+------------+------------+

The combination of StudentID and CourseID together forms a composite key for this table

```

- Primary key
There can be more than one condidate key, we can choose any one not-null condidate key to become primary key.

The primary key in a database table is a special type of key that uniquely identifies each record (row) within that table.

- Alternate key
All condidate keys apart from primary key are Alternate keys.

- Foreign key
It is an attribute which is primary key in some other table

```
                  foreign key                    primary key
                      ⬇️                            ⬇️
    +------------+------------+------------+    +------------+---------------+-----------------+
    | StudentID  | CourseID   | Marks      |    | CourseID   | Course_Name   | Course_Duration |
    +------------+------------+------------+    +------------+---------------+-----------------+
    |    101     |       101  |         90 |    |    101     |           CSE |              6M |
    |    101     |       102  |         78 |    |    102     |           MAT |              6M |
    |    102     |       101  |         45 |    |    103     |           PHY |              3M |
    |    103     |       103  |         90 |    |    104     |           CP  |              9M |
    |    104     |       101  |         45 |    |    105     |           ENG |            1.5M |
    |    104     |       106  |         63 |    |    106     |            DB |              5M |
    +------------+------------+------------+    +------------+---------------+-----------------+

```

