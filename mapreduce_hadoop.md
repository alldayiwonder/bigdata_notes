# Notes on MapReduce and Hadoop

MapReduce is a method of processing large amounts of data for Big Data applications. A very popular implementation of MapReduce is found within Hadoop. So, a distribution such as Hadoop may be used in supplement with relational databases like MySQL and Oracle for Big Data applications (e.g. transactional analysis). A relation can be stored as a file in a distributed file system (DFS) and used within a process such as MapReduce.

### Apache Hadoop

* Inspiried by development at Google that resulting in white papers on their MapReduce and Google File System
* Prominent uses include Yahoo, Facebook, eBay, American Airlines, NYTimes, IBM
* Desiged for scalability
* Components:
  * An alternative file system called Hadoop Distributed File System or HDSF
  * A processing API called MapReduce
  * May include other projects or libraries such as HBase, Hive, or Pig
* Each file in the Hadoop ecosystem is replicated three times on three different pieces of hardware

#### Usage
* Hadoop is an open source platform that is evolving very rapidly
* Enterprises may chose to instead operate a commercial version (e.g. Cloudera, Hortonworks, MapR) which wraps around a portion of the Hadoop distribution and provides additional tools for enterprises.
* A cloud distribution is typically used to implement Hadoop (e.g. Amazon Web Services)

### HBase
* A non-relational database management system that runs on top of HDFS and typically used with Hadoop, and allows for a more concrete way to query and analysis data processed with Hadoop. It provides a sort of quasi-tabular format for users to work through with Hadoop.
* HBase represents data within [wide-column stores](http://db-engines.com/en/article/Wide+Column+Stores). It uses tables stored in HDFS. Each row is specified by a primary key and each column represents an attribute which can multiple contain key, value pairs within the column family. So, an attribute may contain certain key, value pairs in one row and now in another. There is no requirement for each column to contain a given key, value pair.
* There is no schema requirement for data going into HBase, only [schema on read](http://www.techopedia.com/definition/30153/schema-on-read)
* The query language for HBase is Hive (HQL).

### Hue
* User interface for Hadoop

### MapReduce
* Originally created at Google
* Created to solve the problem of how to index and gain meaning from the volume and variety of digital information
* Two components: map and reduce
* Map() function performs an action on all data on **all** nodes (i.e. machine). This execution results in the output of key, value pairs in each node. Since it executes on all nodes simultaneously, the functions are performed in parallel and provides for the massiving scalability that is needed in Big Data application.
* Reduce() function is performed on **some** nodes. This execution will output a combined list by aggregating the outputs of the Map() functions.
* Need to write code that has a Map class, a Reduce class, and a main function with a job that calls an instance of the Map and Reduce classes
* Source data (e.g. HDFS, cloud based) is called upon within the code
* After the Map() function there is an automatic sort and shuffle mechanism built-into the MapReduce program and is not part of the logic that needs to be written by the user within the Map() and Reduce() functions
* Simplest way to optimize a MapReduce process is to add more nodes, and can also modify a wide array of aspects to optimize further

### Hello World for MapReduce
* "Word Count" which takes text as input, produces a list of words, and counts frequency of each word
* Need to define what a word is in your code
* Can be run in an IDE or command line
* Look for word "SUCCESS" in the output along with the results of the processed data

![MapReduce](http://www.cs.uml.edu/~jlu1/doc/source/report/img/MapReduceExample.png)

### Computing with MapReduce
* MapReduce can be used to compute selection, projection, union, intersection, difference, natural join, grouping, aggregations, etc
* The original purpose of MapReduce was to compute very large matrix-vector multiplications, which was needed for Google's [PageRank](http://en.wikipedia.org/wiki/PageRank)
