# Relational Algebra

Operation | Symbol
---------------|------------
PROJECT | Greek letter pi, &pi;
SELECT | Greek letter sigma, &sigma;
RENAME	| Greek letter rho, &rho;
UNION	| Union symbol, &upsilon;
INTERSECTION	| Intersection symbol

### Projection
Queries a selection of a table based on attributes identified, as is done with the SELECT command in SQL.

SQL | Algebra
------- | ------------
SELECT attribute1, attribute2 FROM table | &pi; <sub>attribute1, attribute2</sub> (table)

### Selection
Not to be confused with the SELECT keyword in SQL. Returns those attributes in the table that meet a given criteria.

SQL | Algebra
------- | ------------
SELECT attribute1, attribute2 FROM table WHERE criteria | &pi; <sub>attribute1, attribute2</sub> (&sigma; <sub>criteria</sub> (table))

## Joins
Detailed explanations:
* http://en.wikipedia.org/wiki/Join_%28SQL%29
* http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins

### Cartesian Product (aka Cross Product)
The cartesian product of two tables combines each row in one table with the other table. This results in duplicated rows, so a JOIN is best to combine the two tables in a meaningful way.

SQL | Algebra
------- | ------------
SELECT * FROM table1, table2 | table1 X table2

### Join (aka Inner Join)

SQL | Algebra
------- | ------------
SELECT * FROM table1, table2 WHERE attribute1=attribute2 | &sigma; <sub>attribute1=attribute2</sub> (table1 X table2)

### Natural Join
This is similar to an inner join with duplicated columns removed.
