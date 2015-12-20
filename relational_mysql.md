---
title: Notes on Relational Databases and MySQL
---

# Notes on Relational Databases and MySQL

A relation is a table with attributes, or column headers. Rows of the relation are tuples, and the set of attributes in the relation is the schema.

MySQL is a relational database that can handle large amounts of structured data very well. It can guarantee transactional integrity even as datasets become large and complex through [integrity constraints](http://en.wikipedia.org/wiki/Data_integrity#Types_of_integrity_constraints). However, for Big Data applications, the relational model can only scale upwards; and only to a point at which it then becomes too expensive and complex to perform the application. [Big Data](README.md), in terms of volume, is moving farther away from gigabytes and toward terabytes and petabytes of data. Relational databases may not be able to handle data sets with high velocity or variety, which is common with Big Data. Since MySQL is a relational database, it requires data to be structured with its schema explicitly specified.

Below are notes on how to use MySQL for small data. For Big Data, relational databases will need to be supplemented with other methods and file storage systems. See notes on [MapReduce](mapreduce_hadoop.md).

### Import data into MySQL

[Using LOAD DATA to import data into MySQL](http://cs.nyu.edu/~deena/wp_dbw_fa13/?page_id=483)

Via terminal:

#### Create table example:
```
CREATE TABLE table_name (
	field_name varchar(),
	field_name TIMESTAMP,
	field_name DATE,
	field_name TIME,
	field_name INTEGER
);
```
#### Load data into table example:

For CSV with comma separated values, quotes as text delimiter, and header row:

````
LOAD DATA LOCAL INFILE 'file_path'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 1 LINES;
````
