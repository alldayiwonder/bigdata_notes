# Notes on MapReduce and Hadoop

MapReduce is a method of processing large amounts of data for Big Data applications. A very popular implementation of MapReduce is found within Hadoop. So, a distribution like Hadoop can be used in supplement with relational databases like MySQL and Oracle for Big Data applications (e.g. transactional analysis). A relation can be stored as a file in a distributed file system (DFS) and used within a process such as MapReduce.

### MapReduce
* Created by Google to solve the problem of how to index and gain meaning from the volume and variety of digital information on the web
* The original purpose of MapReduce was to compute very large matrix-vector multiplications, which was needed for Google's [PageRank](http://en.wikipedia.org/wiki/PageRank)
* Two components: map and reduce
* Map() function performs an action on all data on **all** nodes (i.e. machine). This execution results in the output of key, value pairs in each node. Since it executes on all nodes simultaneously, the functions are performed in parallel and provides for the massiving scalability that is needed in Big Data application.
* Reduce() function is performed on **some** nodes. This execution will output a combined list by aggregating the outputs of the Map() functions.
* Need to write code that has a Map class, a Reduce class, and a main function with a job that calls an instance of the Map and Reduce classes
* Source data (e.g. HDFS, cloud based) is called upon within the code
* After the Map() function there is an automatic sort and shuffle mechanism built-into the MapReduce program and is not part of the logic that needs to be written by the user within the Map() and Reduce() functions
* Simplest way to optimize a MapReduce process is to add more nodes, and can also modify a wide array of aspects to optimize further

### Apache Hadoop

* Hadoop is an open source platform that is evolving very rapidly
* Inspiried by the development at Google that resulted in white papers on their MapReduce and Google File System
* Prominent uses include Yahoo, Facebook, eBay, American Airlines, NYTimes, IBM
* Designed for scalability
* Components:
  * An alternative file system called Hadoop Distributed File System or HDSF
  * A processing API called MapReduce
  * May include other projects or libraries such as HBase, Hive, or Pig
* Each file in the Hadoop ecosystem is replicated three times on three different pieces of hardware
* Enterprises may chose to instead operate a commercial version (e.g. Cloudera, Hortonworks, MapR) which wraps around a portion of the Hadoop distribution and provides additional tools for enterprises.
* A cloud distribution is typically used to implement Hadoop (e.g. Amazon Web Services)
* Hadoop operates with the Hadoop distributed file system (HDFS) file system. This means that your local file(s) that you want to input into Hadoop and processed through MapReduce must first be pushed to the HDFS file system.

### Hue
* User interface for Hadoop
* Can browse files that were pushed to HDFS through a GUI

### Hadoop Streaming
* Hadoop is built in Java, so it understands that language natively; but we can also use other langauges to write our Map and Reduce functions.
* Need to run Hadoop through the hadoop-streaming JAR (Java Archive) file, part of Hadoop distribution. This file enables the connection between your Map and Reduce files written in Python and Hadoop based in Java.

### Word Count (the Hello World for MapReduce)
* "Word Count" which takes text as input, produces a list of words, and counts frequency of each word
* Need to define what a word is in your code
* Can be run in an IDE or command line
* Look for word "SUCCESS" in the output along with the results of the processed data

![MapReduce](http://www.cs.uml.edu/~jlu1/doc/source/report/img/MapReduceExample.png)

### Runnning a Word Count within the Cloudera Virtual Machine using Python
The below was done running the [Cloudera VM](http://www.cloudera.com/content/cloudera/en/downloads/quickstart_vms/cdh-5-3-x.html) through [VirtualBox](https://www.virtualbox.org/), which allows you to get started learning or testing your job on Hadoop through the virtual machine. Hadoop and everything is pre-installed on a linux OS.

General procedure via terminal:
* Change directory to the folder containing the map and reduce files written in Python
* Give permission for Hadoop to execute the map and reduce: chmod +x map.py reduce.py
* Since we are using Python, locate the hadoop-streaming JAR file. Within the Cloudera VM, I am using: /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.5.0-mr1-cdh5.3.0.jar
* Push the input file(s) onto HDFS: hadoop fs -put local_path hdfs_path
* Check to see if the file(s) were pushed to the HDFS file system: hadoop fs -ls
* Then this is the command line code to run the job:

        hadoop jar /usr/lib/hadoop-0.20-mapreduce/contrib/streaming/hadoop-streaming-2.5.0-mr1-cdh5.3.0.jar \
        	-D mapreduce.job.reduces=1 \
        	-file map.py \
        	-mapper map.py \
        	-file reduce.py \
        	-reducer reduce.py \
        	-input path-to-input \
        	-output path-to-output

* Note that we are specifying Hadoop to use only a single reducer (-D mapreduce.job.reduces=1) since we are running this in a VM for learning and testing purposes.
* Lastly, the Hadoop job output will be written to HDFS. Copy the output folder to local: hadoop fs -get art_out local_path
