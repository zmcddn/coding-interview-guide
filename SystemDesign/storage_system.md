# File Storage, Block Storage, Object Storage, and HDFS

## File storage

- Data is stored as a single piece of information inside a folder (hierarchical directories structure)
    - Just like you’d organize pieces of paper inside a manila folder
- When you need to access that piece of data, your computer needs to know the path to find it (i.e. `/home/images/beach.jpeg`)

Pros:

- oldest and most widely used data storage system for direct and network-attached storage (NAS) systems
- has broad capabilities and can store just about anything
- great for storing an array of complex files and is fairly fast for users to navigate

Cons:

- File-based storage systems must scale out by adding more systems, rather than scale up by adding more capacity.

## Block storage

- Data is chopped into blocks, each block of data is given a unique identifier, which allows a storage system to place the smaller pieces of data wherever is most convenient.
- Some data can be stored in a Linux environment and some can be stored in a Windows unit.
- When data is requested, the underlying storage software reassembles the blocks of data from these environments and presents them back to the user. 

Pros:

- doesn’t rely on a single path to data, so its fast
- gives the user complete freedom to configure their data
- easy to use and manage, efficient and reliable
- the more data you need to store, the better off you’ll be with block storage.

Cons:

- Can be expensive
- limited capability to handle metadata

## Object storage

- A flat structure in which files are broken into pieces and spread out among hardware.3
- Data is broken into discrete units called objects and is kept in a single repository, instead of being kept as files in folders or as blocks on servers.
- Object storage volumes work as modular units:
    - each is a self-contained repository that owns the data and the metadata that describes the data
    - each has a unique identifier that allows the object to be found over a distributed system
- To retrieve the data, the storage operating system uses the metadata and identifiers
- Can be extremely detailed (i.e. video, photo meta data, etc)
- Object storage requires a simple HTTP API

Pros:

- Cost efficient, pay what you use
- well suited for static data
- can scale to extremely large quantities of data
- good at storing unstructured data.

Cons:

- Objects can’t be modified
- doesn’t work well with traditional databases, because writing objects is a slow process and writing an app to use an object storage API isn’t as simple as using file storage

## Hadoop Distributed File System (HDFS)

- A distributed file system designed to run on commodity hardware.
- It stores each file as a sequence of blocks
    - all blocks in a file except the last block are the same size. 
    - The blocks of a file are replicated for fault tolerance (HDFS requires Block Storage)
    - The block size and replication factor are configurable per file.
- Files in HDFS are write-once and have strictly one writer at any time.

Pros:

- highly fault-tolerant and is designed to be deployed on low-cost hardware
- provides high throughput access to application data and is suitable for applications that have large data sets
- Enables streaming access to file system data

Cons:

- Problems with small files
- the data read or write done from the disk which makes it difficult to perform in-memory calculation and lead to processing overhead or High up processing.
- Supports Only Batch Processing

### Map Reduce

- MapReduce is a programming model or pattern within the Hadoop framework that is used to access big data stored in the HDFS.
- It is a core component, integral to the functioning of the Hadoop framework.
- With MapReduce, rather than sending data to where the application or logic resides, the logic is executed on the server where the data already resides, to expedite processing.

How does it work:

- Essentially there are two functions: **Map** and **Reduce**
- The **Map** function takes input from the disk as `<key,value>` pairs, processes them, and produces another set of intermediate `<key,value>` pairs as output.
- The **Reduce** function also takes inputs as `<key,value>` pairs, and produces `<key,value>` pairs as output.
- **Combine** is an optional process. 
    - The combiner is a reducer that runs individually on each mapper server. 
    - It reduces the data on each mapper further to a simplified form before passing it downstream.
- **Partition** is the process that translates the `<key, value>` pairs resulting from mappers to another set of `<key, value>` pairs to feed into the reducer. 
    - It decides how the data has to be presented to the reducer and also assigns it to a particular reducer.

## Database vs Storage Systems

Conclusion: you shouldn't use database for file storage, mainly because of performance

- [Database vs File system storage - Stack Overflow](https://stackoverflow.com/questions/38120895/database-vs-file-system-storage)
- [Is it a bad practice to store large files (10 MB) in a database? - Software Engineering Stack Exchange](https://softwareengineering.stackexchange.com/questions/150669/is-it-a-bad-practice-to-store-large-files-10-mb-in-a-database)


## Reference:

- [File storage, block storage, or object storage?](https://www.redhat.com/en/topics/data-storage/file-block-object-storage)
- [System Design — Storage. Storage concepts and considerations in… \| by Larry | Peng Yang | Computer Science Fundamentals | Medium](https://medium.com/must-know-computer-science/system-desing-storage-d8ef4a8d952c)
- [Hadoop - Pros and Cons - GeeksforGeeks](https://www.geeksforgeeks.org/hadoop-pros-and-cons/)
- [Hadoop In 5 Minutes \| What Is Hadoop? | Introduction To Hadoop | Hadoop Explained |Simplilearn - YouTube](https://www.youtube.com/watch?v=aReuLtY0YMI&ab_channel=Simplilearn)
- [MapReduce 101: What It Is & How to Get Started - Talend](https://www.talend.com/resources/what-is-mapreduce/)
