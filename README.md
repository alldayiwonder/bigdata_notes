# What is Big Data?
There is no formal definition for "Big Data." As with the term "green," this can bring about confusion; it can also lead some to believe that they are working with big data when they, for all practical purposes, are actually using small data.

## The common definition of Big Data

### Volume, velocty, variety
As described by Doug Laney in a 2001 [article](http://blogs.gartner.com/doug-laney/files/2012/01/ad949-3D-Data-Management-Controlling-Data-Volume-Velocity-and-Variety.pdf).

1. Volume: data is too big to work with on a single machine. Since this is relative to the latest in personal computing power, the absolute volume will increase over time. So the definition of Big Data is influenced by Moore's Law. 
2. Velocity: data is too dynamic and being created at too high of a rate (e.g. tweets per second) for a single machine to handle.
3. Variety: (e.g. unstructuerd data, NoSQL databases, etc)

If you have all three cases, you are dealing with big data under this common definition. If you have only one case, it is likely you are still dealing with big data.

### Practical differences between small and big data
As described by Jules Berman in [Principles of Big Data](http://www.sciencedirect.com/science/book/9780124045767).

| Small Data                                              | Big Data                                |
| ---------------------------------------                 |:---------------------------------------:| 
| Gathered for a specific goal                            | May or may not have a goal initially, or may change with time | 
| Exists in one location, often in a single file          | Can be in multiple files and across multiple machines in different geographic locations      | 
| Highly structured (e.g. spreadsheet, csv)               | May be unstructured, in a variety of different formats, and multi-disicplinary     |   
| Prepared by end user for own purposes                   | May be prepared by one group, analyzed by a second, and used by third group  | 
| Kept for a finite timeframe for project with clear endpoint (maybe 5 or 10 years in government or academia)         | May keep data indefinitely or with uncertain lifespan | 
| Data measured or recorded with a single protocol and units  | Data may be collected using a variety of protocols and units  throughout different geographical regions | 
| Can typically be reproduced                            | May not be reproducible | 
| Cost of failure or losing data is small                | Cost of failure or losing data can be high | 
| Data describes itself in an important way              | May have to clean data thoroughly and filter out bogus information | 
| Can analyze all the data at once from a single file or machine  | May have to deal with portions of data and aggregate results | 
