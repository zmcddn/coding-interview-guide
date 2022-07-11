# NoSQL databases

## NoSQL database types

- **Key-value stores**: simplest, item stored in the form of key/value pairs. Each Key is unique and accepts only strings, whereas the value corresponding to the particular Key can accept String, JSON, XML, etc.
    - **Use Case**: Session info, user preference, shopping carts, produce recommendations, etc
    - **Products**: Redis, Voldemort, Riak, and Amazon’s Dynamo
- **Document stores**: extension of key-value store, pair each key with a complex data structure known as a document (i.e. JSON, XML, etc)
    - **Use Case**: User profiles, Management of content, etc
    - **Products**: MongoDB and CouchDB
- **Column-oriented database**: store columns of data together instead of rows and are optimized for queries over large datasets
    - **Use Case**: User Preferences, Business Intelligence, Managing data warehouses, etc 
    - **Products**: Cassandra, HBase, Hypertable, Google's BigTable
- **Graph database**: store information about networks, such as social connections
    - **Use Case**: Social Networking, Recommendation Engine, Logistics, Risk Assessment, Fraud detection, etc
    - **Products**: Neo4J and HyperGraphDB 

## NoSQL database features

- Different types for different use case
- Distributed
- Flexible Schema
- Eliminated Downtime
- High Scalability

## Cassandra

- Cassandra is de-centralized, which means all nodes are the same (its called **server-symmetry**). There is no leader-follower structure, all the nodes follows P2P (peer to peer) gossip protocol, so its **highly available**
- Cassandra is **highly scalable**, new node will automatically be discovered and there is no reboot needed

## Cassandra vs MongoDB

| Difference | Cassandra | MongoDB |
| :--------: | :-------: | :-----: |
| DB structure | Unstructured data | JSON-like documents |
| Index | Primary Key, but no secondary indexes supported | Index, if no index then each file is searched which could slow down read times |
| Query | CQL (like SQL) | More like programming |
| Replication | leader-leader | leader-follower with auto-election |



## Reference

- [NoSQL Database Types - DZone Database](https://dzone.com/articles/nosql-database-types-1)
- [4 Types of NoSQL Databases & When to use them?](https://www.blazeclan.com/blog/dive-deep-types-nosql-databases/)
- [A Comprehensive Guide to Cassandra Architecture](https://www.instaclustr.com/cassandra-architecture/)
- [Cassandra vs MongoDB in 2018](https://blog.panoply.io/cassandra-vs-mongodb)
- [Cassandra vs. MongoDB vs. Hbase: A Comparison of NoSQL Databases \| Logz.io](https://logz.io/blog/nosql-database-comparison/)
- [Introduction to Amazon DynamoDB for Cassandra developers \| AWS Database Blog](https://aws.amazon.com/blogs/database/introduction-to-amazon-dynamodb-for-cassandra-developers/)
- [Amazon DynamoDB Under the Hood: How We Built a Hyper-Scale Database](https://www.youtube.com/watch?v=yvBR71D0nAQ&ab_channel=AmazonWebServices)
- [Amazon DynamoDB Deep Dive: Advanced Design Patterns for DynamoDB](https://www.youtube.com/watch?v=HaEPXoXVf2k&ab_channel=AmazonWebServices)
- [HBase Tutorial for Beginners: Learn in 3 Days!](https://www.guru99.com/hbase-tutorials.html)
