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

---

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