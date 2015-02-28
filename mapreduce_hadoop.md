# Notes on MapReduce and Hadoop

MapReduce is a method of processing large amounts of data for Big Data applications. A very popular implementation of MapReduce is found within Hadoop. So, a distribution such as Hadoop may be used in supplement with relational databases like MySQL and Oracle for Big Data applications (e.g. transactional analysis).

### Apache Hadoop

* Inspiried by development at Google that resulting in white papers on their MapReduce and Google File System
* Prominent uses include Yahoo, Facebook, eBay, American Airlines, NYTimes, IBM
* Desiged for scalability
* Components:
  * An alternative file system called Hadoop Distributed File System or HDSF
  * A processing API called MapReduce
  * May include other projects or libraries such as HBase, Hive, or Pig
* Each file in the Hadoop ecosystem is replicated three times on three different pieces of hardware

### Usage
* Hadoop is an open source platform that is evolving very rapidly
* Enterprises may chose to instead operate a commercial version (e.g. Cloudera, Hortonworks, MapR) which wraps around a portion of the Hadoop distribution and provides additional tools for enterprises.
* A cloud distribution is typically used to implement Hadoop (e.g. Amazon Web Services)

### HBase
* A non-relational database management system that runs on top of HDFS and typically used with Hadoop, and allows for a more concrete way to query and analysis data processed with Hadoop. It provides a sort of quasi-tabular format for users to work through with Hadoop.
* HBase represents data within [wide-column stores](http://db-engines.com/en/article/Wide+Column+Stores). It uses tables stored in HDFS. Each row is specified by a primary key and each column represents an attribute which can multiple contain key, value pairs within the column family. So, an attribute may contain certain key, value pairs in one row and now in another. There is no requirement for each column to contain a given key, value pair.
* There is no schema requirement for data going into HBase, only [schema on read](http://www.techopedia.com/definition/30153/schema-on-read)
* The query language for HBase is Hive (HQL).

### MapReduce
