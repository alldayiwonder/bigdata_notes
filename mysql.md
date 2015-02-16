# Notes on MySQL

While MySQL can handle the large volume aspect of [Big Data](README.md), it may not be able to handle data sets with high velocity or variety. Since MySQL is a relational database, it requires data to be structured with its schema explicitly specified.

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

