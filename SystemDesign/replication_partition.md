# Replication & Partition

- Replication
    - Leader-follower
    - Multi-leader
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
    - Leaderless
        - How to catch up when node comes back: user versions
            - Read repair: repair node when clients read based on version number
            - Anti-entropy process: background process constantly look for difference
        - Quorum
            - For ***N*** nodes, its considered as successful if
            - each write has ***W*** writes confirmed successful
            - there is at lease ***R*** nodes for read
            - such that ***W + R > N***

- Partition: query throughput can be scaled by adding more nodes
    - For key-value store
        - Partition by key range (i.e. alphabetical) and keep sorted in each partition
            - may result in skew or hot spot
        - Partition by hash of key
            - Looses the ability to do efficient range queries
    - Handle skew and hot spots
        - if one key is known to be very hot, a simple technique is to add a random number to the beginning or end of the key
    - Strategies for rebalancing partitions
        - Hash mod N, need to use fixed number of partition, otherwise scale up will result in different result
        - Dynamic partitioning, with respect to a configured size
    - Coordination service (keep track of cluster metadata) to route request


Reference:

- [Designing Data-Intensive Applications](https://www.amazon.ca/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321/ref=sr_1_1?dchild=1&gclid=Cj0KCQjw_8mHBhClARIsABfFgpg5q5IQvE2s5OBULx6LQFDETV41haS67EE3JAfvobPADJUJHN7dUbsaAjjrEALw_wcB&hvadid=285888202784&hvdev=c&hvlocphy=9001327&hvnetw=g&hvqmt=e&hvrand=12070511852976413586&hvtargid=kwd-407664346480&hydadcr=16109_9598899&keywords=design+data+intensive+application&qid=1626587742&sr=8-1)
