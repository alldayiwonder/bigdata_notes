# Notes on Relational Databases and MySQL

MySQL is a relational database that can handle large amounts of structured data very well. However, for Big Data application, it can scale upwards in terms of data volume only up to a point at which it then becomes too expensive and complex. [Big Data](README.md), in terms of volume, is moving farther away from gigabytes and toward terabytes and petabytes of data. Relational databases may not be able to handle data sets with high velocity or variety, which is common with Big Data. Since MySQL is a relational database, it requires data to be structured with its schema explicitly specified.

So, keeping in mind the above limitations, a relational database like MySQL will likely not be used for Big Data application. Below are notes on how to use MySQL for small data. For Big Data, relational databases should be supplemented with other methods and file storage systems. See notes on [MapReduce](mapreduce_hadoop.md).

### Import data into MySQL

Via terminal:

#### Create table:
```
CREATE TABLE table_name (
	field_name varchar(),
	field_name TIMESTAMP,
	field_name DATE,
	field_name TIME,
	field_name INTEGER
);
```
#### Load data into table:

Example for CSV with comma separated values and quotes as text delimiter:

````
LOAD DATA LOCAL INFILE 'file_path'
INTO TABLE table_name
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\r\n'
IGNORE 1 LINES;
````
