# hello-world
test repo from tutorial

I'm adding some sample information to test this thing out.

This line I added from sublime.

## hello!


# IBM SQL 101

This folder contains files related to IBM's cognitive training SQL 101 course taken as part of DevUp training. Uses DB2 Warehouse RMDBS

## Table Basics

### There are 5 basic commands
1. Create
2. Insert
3. Select
4. Update
5. Delete

## IBM DB2 Warehouse Credentials

```json
{
  "hostname": "dashdb-entry-yp-dal09-09.services.dal.bluemix.net",
  "password": "tkmcG_H3G_D7",
  "https_url": "https://dashdb-entry-yp-dal09-09.services.dal.bluemix.net:8443",
  "port": 50000,
  "ssldsn": "DATABASE=BLUDB;HOSTNAME=dashdb-entry-yp-dal09-09.services.dal.bluemix.net;PORT=50001;PROTOCOL=TCPIP;UID=dash11391;PWD=tkmcG_H3G_D7;Security=SSL;",
  "host": "dashdb-entry-yp-dal09-09.services.dal.bluemix.net",
  "jdbcurl": "jdbc:db2://dashdb-entry-yp-dal09-09.services.dal.bluemix.net:50000/BLUDB",
  "uri": "db2://dash11391:tkmcG_H3G_D7@dashdb-entry-yp-dal09-09.services.dal.bluemix.net:50000/BLUDB",
  "db": "BLUDB",
  "dsn": "DATABASE=BLUDB;HOSTNAME=dashdb-entry-yp-dal09-09.services.dal.bluemix.net;PORT=50000;PROTOCOL=TCPIP;UID=dash11391;PWD=tkmcG_H3G_D7;",
  "username": "dash11391",
  "ssljdbcurl": "jdbc:db2://dashdb-entry-yp-dal09-09.services.dal.bluemix.net:50001/BLUDB:sslConnection=true;"
}
```

## DDL Data Definition Language

### Create

```SQL
CREATE TABLE tablename
	(attribute1 characterSet constraints,
	 attribute2 charSet, constraints,
	 attributte3 charSet, constraints
	)
```

### Create Schema
A SQL schema is identified by a schema name, and includes a authorization identifier to indicate the user or account who owns the schema. Schema elements include tables, constraints, views, domains and other constructs that describe the schema.

A schema is created using the CREATE SCHEMA statement. For example, we can create a schema called LIBRARY for this course:
 
CREATE SCHEMA LIBRARY AUTHORIZATION ‘Robert’
 
The data types used can be: numeric, character-string, bit-string, Boolean, DATE, timestamp, etc.

## DML Data Manipulation Language

### Insert

```SQL
INSERT INTO [tablename]
([Columname],...)
VALUES([Value],...)
VALUES([Value2],...)
...
```

### Select

```SQL
SELECT attribute list
FROM table list
WHERE condition
```
ex - `SELECT * FROM tablename` to get the whole table
comparison operators supported by a RMDBS:
* = 
* \>
* <
* \>=
* <=
* <> (not equal to)

#### Select Statement string patters, ranges, sets
use `like` predicate
for example 
```SQL
SELECT firstname from author
where firstname like 'R%'
```
or 

```SQL
 WHERE pages BETWEEN 290 AND 300`
```
or 
```SQL
WHERE country IN ('US', 'UK')
```

### Update

```SQL
UPDATE [tablename]
SET [[columnname]=[value]]
WHERE [condition]
```
if you don't specify the where clause, all rows will be updated

### Delete

```SQL
DELETE FROM [tablename]
WHERE [condition]
```
if you don't specify the where clause, all rows will be deleted



## Sorting and Grouping 

add `ORDER BY colummname condition` in `SELECT` statement
can append condition `desc` for descending order 
can replace columnname with a number representing the number of the column you want in the above select statement

add `GROUP BY ` in `SELECT` statement 


avoid duplicates 
```SQL
SELECT DISTINCT(columnname) FROM tablename
```
or 
```SQL
SELECT columnname, COUNT(columnname) AS columnname2 FROM tablename GROUP BY columnname
```
to get a count of the duplicates and group them into the subsets defined by duplicates in specified columnname
can add the `AS` to name the calculated COUNT column

add conditions to GROUP BY with HAVING clause
HAVING only works with GROUP BY

```SQL
select columnname, count(columnname) as columnname2
from tablename group by columnname having count(columnname) > 4
```



### Extra Info

CREATE TABLE Statement

The CREATE TABLE statement includes these clauses:

·       DEFAULT
·       CHECK

Use the DEFAULT clause in the CREATE TABLE statement to specify the default value for the database server to insert into a column when no explicit value for the column is specified.

This syntax fragment is part of the Column definition.

DEFAULT Clause

```
|--DEFAULT------------------------------------------------------>

>--+-+-NULL---------+--------------------------------------------+--|
   | +-label--------+                                            |   
   | +-literal------+                                            |   
   | +-USER---------+                                            |   
   | '-CURRENT_USER-'                                            |   
   |  (1)                                                        |   
   '-------+-+-CURRENT-+--+----------------------------------+-+-'   
           | '-SYSDATE-'  |                              (2) | |     
           |              '-| DATETIME Field Qualifier |-----' |     
           +-TODAY---------------------------------------------+     
           +-SITENAME------------------------------------------+     
           '-DBSERVERNAME--------------------------------------'     

```

Use the CHECK clause to designate conditions that must be met before data can be assigned to a column during an INSERT or UPDATE statement.

This syntax fragment is part of the Single-Column Constraint Format and the Multiple-Column Constraint Format.

CHECK Clause
```

                           (1)      
|--CHECK--(--| Condition |------)-------------------------------|

```

Notes:

    See Condition

The condition cannot include a user-defined routine.

During an insert or update, if the check constraint of a row evaluates to false, the database server returns an error. The database server does not return an error if a row evaluates to NULL for a check constraint. In some cases, you might want to use both a check constraint and a NOT NULL constraint.
Condition

Use a condition to test whether data meets certain qualifications. Use this segment wherever you see a reference to a condition in a syntax diagram.

Condition
```
   .-Logical_Operator-----------------------------.   
   V                                      (1)     |   
|----+-----+--+-| Comparison Conditions |-------+-+-------------|
     '-NOT-'  |                             (2) |     
              +-| Condition with Subquery |-----+     
              |                           (3)   |     
              '-| User-Defined Function |-------'     
```

SELECT Statement

The basic structure of the SELECT statement is formed from three clauses: SELECT, FROM and WHERE.
<attribute list> is a list of attribute names whose values are to be retrieved by the query
<table list> is a list of the relation names required to process the query
<condition> is a conditional(Boolean) expression that identifies the tuples to be retrieved by the query

In situations where you might want to use multiple IF-THEN-ELSE statements, you can often use a single SELECT statement instead. The SELECT statement allows a CLIST to select actions from a list of possible actions. An action consists of one or more statements or commands. The SELECT statement has the following syntax, ending with the END statement. You can use the SELECT statement with or without the initial test expression.

Read syntax diagramSkip visual syntax diagramSelect

```SQL
SELECT [test expression]
	WHEN [expression1]
	...
		(action)
	...
	WHEN [expression2]
	WHEN [expression3]
	...
	[OTHERWISE]
	...
		(action)
	...
END
```


