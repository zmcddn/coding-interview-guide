# Replication & Partition

## Replication

### Leader-follower (single-leader)

- Writes are only accepted on the leader, followers are read only
- Synchronous Replication: the leader waits until follower has confirmed that it received the write before reporting success to the user, and before making the write visible to other clients
- Asynchronous Replication: the leader sends the message, but doesn’t wait for a response from the follower.
- Setting Up New Followers: 
    - Take a consistent snapshot of the leader’s database at some point in time
    - Copy the snapshot to the new follower node
    - The follower connects to the leader and requests all the data changes that have happened since the snapshot was taken (according to leader’s replication log)
- Handling Node Outages
    - Follower failure: Catch-up recovery
        - Similar to setting up new followers, each follower keeps a log of the data changes it has received from the leader, so we know where it was stopped
    - Leader failure: Failover - one of the followers needs to be promoted to be the new leader manually or automatically
        - Determining that the leader has failed (i.e. timeout: if a node doesn’t respond for some period of time).
        - Choosing a new leader: the best candidate is usually the replica with the most up-to-date data changes from the old leader
        - Reconfiguring the system to use the new leader
- Implementation of Replication Logs
    - Statement-based replication: leader logs every write request (statement) that it executes and sends that statement log to its followers
        - Random, time, custom functions may go wrong 
    - Write-ahead log (WAL) shipping: every write is appended to a log
        - Replication is closely coupled to the storage engine (of the logs)
    - Logical (row-based) log replication: use different log formats for replication and for the storage engine
    - Trigger-based replication: only replicate a subset of the data
- **Eventual consistency**: if an application reads from an asynchronous follower, it may see outdated information if the follower has fallen behind, but the followers will eventually catch up and become consistent with the leader

### Multi-leader

- Multi-leader replication
    - Circular topology
    - Star topology
    - All-to-all topology
- Write conflict resolve
    - make sure all writes for a particular record go through the same leader
    - Unique-write ID: last write win (LWW)
    - Unique-replica ID: writes with higher numbered replica wins
    - Somehow merge conflicts
    - Record and solve/report later
    - Custom conflict resolution:
        - On-write: db detects conflict in the log and calls the conflict handler
        - On-read: all conflicting writes are stored, next time data is read all versions are returned to the application for user to solve or automatically resolve, and write the result back to db.
    - Automatic conflict resolve
        - Conflict free replicated datatypes (CRDT)
        - Mergeable persistent data structures
        - Operational transformation (google doc)


### Leaderless

- How to catch up when node comes back: user versions
    - Read repair: repair node when clients read based on version number
    - Anti-entropy process: background process constantly look for difference
- **Quorum Consistency**
    - For ***N*** nodes, its considered as successful if
    - each write has ***W*** writes confirmed successful
    - there is at lease ***R*** nodes for read
    - such that ***W + R > N***
- **Sloppy quorum**: writes and reads still require *w* and *r* successful responses, but those may include nodes that are among the designated *n*  nodes for a value
- **Hinted handoff**: Once the network interruption is fixed, any writes that one node temporarily accepted on behalf of another node are sent to the appropriate “home” nodes


## Partition (sharding): query throughput can be scaled by adding more nodes

- For key-value store
    - Partition by key range (i.e. alphabetical) and keep sorted in each partition
        - may result in skew or hot spot
            - Solution: Could use a combined key
            - For example, you could prefix each timestamp with the sensor name so that the partitioning is first by name and then by time
    - Partition by hash of key (uniformly distributed)
        - Looses the ability to do efficient range queries
            - Solution: **compound primary key** consisting of several columns
            - For example, only the first part of that key is hashed to determine the partition, the other columns are used as a concatenated index for sorting the data

- Handle skew and hot spots: responsibility of the application
    - if one key is known to be very hot, a simple technique is to add a random number to the beginning or end of the key
        - it only makes sense to append the random number for the small number of hot keys
        - need some way of keeping track of which keys are being split

- Partitioning and Secondary Indexes
    - Partitioning Secondary Indexes by Document (***local index***)
        - each partition is completely separate: each partition maintains its own secondary indexes, covering only the documents in that partition
        - doesn’t care what data is stored in other partitions
        - **scatter/gather** problem: read queries on secondary indexes on partitioned database needs to query to all partitions
    - Partitioning Secondary Indexes by Term (***global index***)
        - a global index that covers data in all partitions, and the global index must also be partitioned but can be different from the primary key index
        - We call this kind of index term-partitioned, because the term we’re looking for determines the partition of the index
        - Reads faster but writes slower and complex
        - updates to global secondary indexes are often asynchronous

- Strategies for rebalancing partitions
    - Do NOT use Hash mod N since it can result in different result
    - Use fixed number of partition, create many more partitions than nodes and assign several partitions to each node
    - Dynamic partitioning, auto-partition when 
        - existing partition reach a configured size
        - the number of partitions is proportional to the size of the dataset
        - the number of partitions proportional to the number of nodes

- Request Routing among partitions and nodes
    - Coordination service (keep track of cluster metadata) to route request (i.e. zookeeper)
    - **gossip protocol**: Requests can be sent to any node, and that node forwards them to the appropriate node for the requested partition


Reference:

- [Designing Data-Intensive Applications](https://www.amazon.ca/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321/ref=sr_1_1?dchild=1&gclid=Cj0KCQjw_8mHBhClARIsABfFgpg5q5IQvE2s5OBULx6LQFDETV41haS67EE3JAfvobPADJUJHN7dUbsaAjjrEALw_wcB&hvadid=285888202784&hvdev=c&hvlocphy=9001327&hvnetw=g&hvqmt=e&hvrand=12070511852976413586&hvtargid=kwd-407664346480&hydadcr=16109_9598899&keywords=design+data+intensive+application&qid=1626587742&sr=8-1)
