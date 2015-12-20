# Notes on Big Data

[Relational Databases and MySQL](relational_mysql.md)

[MapReduce Hadoop](mapreduce_hadoop.md)

[Natural Join with MapReduce](natural_join_mapreduce.md)

[Frequent Itemsets for Mining Data](frequent_itemsets.md)

[Similar Items](similar_items.md)

[Matrix-Vector Multiplication with MapReduce](matrix_multiplication.md)

# What is Big Data?
As of 2015, there is no formal definition for the term "Big Data." This tends to cause a good deal of confusion, while at the same time presenting an exciting new field. Some may be lead to believe they are working with big data when they are using small data.

We find a similar issue with the term "green" used in the field of sustainability, and which also lacks any standard definition. And as with something claimed as being green, big data may also be subject to the equivalent of [greenwashing](http://en.wikipedia.org/wiki/Greenwashing), where organizations may use it solely as a buzz word.

## The Common Definition of Big Data

### Volume, Velocity, Variety (The Three V's)
As described by Doug Laney in a 2001 [article](http://blogs.gartner.com/doug-laney/files/2012/01/ad949-3D-Data-Management-Controlling-Data-Volume-Velocity-and-Variety.pdf).

1. Volume: data is too big to work with on a single machine.
2. Velocity: data is too dynamic and being created at too high of a rate (e.g. tweets per second) for a single machine to handle.
3. Variety: (e.g. unstructured data, NoSQL databases, etc)

The first two points are relative to processing power and the latest technology in personal computing, the absolute volume or velocity that may identify Big Data will increase over time. And so this definition of Big Data is fluid and influenced by [Moore's Law](http://en.wikipedia.org/wiki/Moore%27s_law).

If you have all three cases, you are dealing with big data under this common definition. If you have only one case, it is likely you are still dealing with big data.

Examples having an instance of only one of the three V's:

| Case                | Example             |
| --------------------| --------------------|
| Volume          | Genetics (structured, high volume of data)                    |
| Velocity        | Earthquake detection data (e.g. streaming data, not necessarily stored) |
| Variety         | Facial recognition data (may be static)                               |

### Small Data vs Big Data
As described by Jules Berman in [Principles of Big Data](http://www.sciencedirect.com/science/book/9780124045767).

| Small Data                                              | Big Data                                |
| ---------------------------------------                 |---------------------------------------|
| Gathered for a specific goal                            | May or may not have a goal initially, or may change with time |
| Exists in one location, often in a single file          | Can be in multiple files and across multiple machines in different geographic locations      |
| Highly structured (e.g. spreadsheet, csv)               | May be unstructured, in a variety of different formats, and multi-disicplinary     |
| Prepared by end user for own purposes                   | May be prepared by one group, analyzed by a second, and used by third group  |
| Kept for a finite time frame for project with clear endpoint (maybe 5 or 10 years in government or academia)         | May keep data indefinitely or with uncertain lifespan |
| Data measured or recorded with a single protocol and units  | Data may be collected using a variety of protocols and units  throughout different geographical regions |
| Can typically be reproduced                            | May not be reproducible |
| Cost of failure or losing data is small                | Cost of failure or losing data can be high |
| Data describes itself in an important way              | May have to clean data thoroughly and filter out bogus information |
| Can analyze all the data at once from a single file or machine  | May have to deal with portions of data and aggregate results |

# Sources of Data

* Human: data initiated by a human such as social network posts, cell phone calls, online purchases, and the metadata created alongside such data.
* Machine: communication between machines that may never be seen by humans (e.g. internet of things)

# What is Data Science?

[![data-science-venn-diagram](http://static1.squarespace.com/static/5150aec6e4b0e340ec52710a/t/51525c33e4b0b3e0d10f77ab/1364352052403/Data_Science_VD.png?format=750w "Data Science Venn Diagram")](http://drewconway.com/zia/2013/3/26/the-data-science-venn-diagram)

[![analyzing-the-analyzers](https://www.safaribooksonline.com/library/view/doing-data-science/9781449363871/images/dnds_0104.png "Sub Fields of Data Science")](http://www.oreilly.com/data/free/analyzing-the-analyzers.csp)

Harlan Harris’s clustering and visualization of subfields of data science from Analyzing the Analyzers (O’Reilly) by Harlan Harris, Sean Murphy, and Marck Vaisman based on a survey of several hundred data science practitioners in mid-2012
