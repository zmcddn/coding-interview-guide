# Transaction & Isolation

## Transaction

- Transaction
    - A transaction is a way for an application to group several reads and writes together into a logical unit.
    - all the reads and writes in a transaction are executed as one operation: either the entire  transaction succeeds (commit) or it fails (abort, rollback).

### ACID (Atomicity, Consistency, Isolation, and Durability)

- Atomicity
    - describes what happens if a client wants to make several writes, but a fault occurs after some of the writes have been processed (gives all-or-nothing guarantee)
        - if the writes are grouped together into an atomic transaction, and the transaction cannot be completed (committed) due to a fault, then the transaction is aborted and the database must discard or undo any writes it has made so far in that transaction.
    - Without atomicity, if an error occurs, it’s difficult to know which changes have taken effect and which haven’t.

- Consistency
    - the idea is that you have certain statements about your data (invariants) that must always be true
    - However, this idea of consistency depends on the application’s notion of invariants (This is not something that the database can guarantee)

- Isolation
    - Most databases are accessed by several clients at the same time, isolation is used to handle concurrency problems (race conditions)
    - it means that concurrently executing transactions are isolated from each other: they cannot step on each other’s toes
    - In theory textbooks formalize isolation as serializability, which mean transactions happen one by one
    - In practice, serializable isolation is rarely used, because it carries a performance
penalty

- Durability
    - ensures that once a transaction has committed successfully, any data it has written will not be  forgotten (regardless of failures and crashes).
    - In a single-node database, durability typically means that the data has been written to nonvolatile storage such as a hard drive or SSD.
        - It usually has a write-ahead log (or similar) for recovery
    - In a replicated database, durability may mean that the data has been successfully copied to some number of nodes.
        - a database must wait until these writes or replications are complete before reporting a transaction as successfully committed
    - Replication durability cases:
        - if write to disk and machine dies, data is inaccessible until you fix it, but replicated system remain available
        - If a node crashes on a particular input, all replicas can be down, in memory data will be lost
        - In an asynchronously replicated system, recent writes may be lost when the leader becomes unavailable
        - Hardware disks may not be reliable (SSD due to power cut, firmware issues, etc)
        - File maybe corrupted after a crash due to software (file system, storage engine, etc) bugs

## Isolation

### Weak Isolation

- **Read Committed**: 
    - Two guarantees
        1. No dirty reads: When reading from the database, you will only see data that has been committed.
            - dirty reads: read uncommitted data from other transaction
        2. No dirty writes: When writing to the database, you will only overwrite data that has been committed.
            - dirty writes: later write overwrites an (earlier) uncommitted value
    - Implementation
        - Row level locks (to prevent dirty write): 
            - acquire a lock on the project (when updating), hold lock until transaction is committed or aborted. 
            - Only one transaction can hold a lock for any given object, others must wait
        - To prevent dirty read:
            - only see the old value (not the new value that is being committing to database)
            - Only when the new value is committed do transactions switch over to reading the new value.
        - Typically read committed uses a separate snapshot for each query

- **read skew (nonrepeatable read)**
    - when two transactions are processing into different database, one can read the database in an inconsistent state. But once the transaction is complete, the values will be consistent
    - Read skew is considered acceptable under read committed isolation
    - this may be a problem for database backups or Analytic queries and integrity checks
    
- **Snapshot isolation** is the most common solution to read skew
    - Transaction sees all the data that was committed in the database at the start of transaction
    - each transaction sees only the old data from that particular point in time
    - Implementation: ***multiversion concurrency control (MVCC)***
        - From a performance point of view, a key principle of snapshot isolation is readers never block writers, and writers never block readers
        - database must potentially keep several different committed versions of an object
        - Typically snapshot isolation uses the same snapshot for an entire transaction
    - readers never block writers, and writers never block readers

- MVCC implementation (for postgres)
    - When a transaction is started, it is given a unique, always-increasing transaction ID (*txid*).
    - Whenever a transaction writes anything to the database, the data it writes is tagged with the transaction ID of the writer.
    - Each row in a table has a *created_by* field, containing the ID of the transaction that inserted this row into the table
    - each row has a *deleted_by* field (initially empty)
    - If a transaction deletes a row, row is soft deleted by marking the *deleted_by* field to the ID of the transaction that requested the deletion (row is not deleted from database)
    - when it is certain that no transaction can any longer access the deleted data, a garbage collection process in the database removes the soft deleted rows
    - An update is internally translated into a delete and a create.
    - transaction IDs are used to decide which objects it can see and which are invisible for reads. Visibility rules for both creation and deletion:
        - At the time when the reader’s transaction started, the transaction that created the object had already committed
        - The object is not marked for deletion, or if it is, the transaction that requested deletion had not yet committed at the time when the reader’s transaction started.
    - By never updating values in place but instead creating a new version every time a value is changed, the database can provide a consistent snapshot while incurring only a small overhead.
    - Database index point to all versions of an object and filter out those invisible ones

- To prevent **Lost update** (in a read-modify-write cycle): when two transactions do this concurrently, one of the modifications can be lost
    - Atomic update operations: taking an exclusive lock on the object when it is read so that no other transaction can read it until the update has been applied (***cursor stability***).
    - Explicit locking: explicitly lock objects that are going to be updated
    - Automatically detecting lost updates: allow transactions to execute in parallel, abort transaction and force it to retry if lost updated is detected
    - Compare-and-set: allow an update to happen only if the value has not changed since you last read it. If it changes, force retry.
    - For replicated databases: allow concurrent writes to create several conflicting versions of a value (also known as siblings), and to use application code or special data structures to resolve and merge these versions after the fact.

- **Write Skew**: if two transactions read the same objects, and then update some of those objects (different transactions may update different objects), then dirty write or lost update may happen
    - Solution: explicitly lock the rows that the transaction depends on 
        - **Lock the row for update**
        - **Unique constraint for create**

- **phantom**: a write in one transaction changes the result of a search query in another transaction (i.e. objects that do not yet exist in the database, but which might be added in the future)
    - A serializable isolation level is much preferable in most cases
    - **materializing conflicts** (last resort if no alternative is possible): it takes a phantom and turns it into a lock conflict on a concrete set of rows that exist in the database (i.e. pre-create all the rows for different combinations in database, and new inquires becomes checking the existing rows rather than create them)


### Serializable isolation (strongest isolation level)

- Literally executing transactions in a serial order
    - single-threaded execution
    - **stored procedure**: the application submit the entire transaction code to the database ahead of time, and executing all transactions on a single thread (in-memory)

- **Two-phase locking (2PL)** 
    - ***pessimistic*** concurrency control mechanism: if anything may go wrong, it's better to wait until its safe to do anything (similar to *mutual exclusion*)
    - Concurrent transactions are allowed to read the same object when nobody is writing to it. 
    - When a write happens (update/delete): 
        - the second transaction (can be read or write) must wait until first transaction (can be read or write) commits or aborts
        - Reading an old version is forbidden
        - writers don’t just block other writers; they also block readers and vice versa
    - Implementation: lock (in shared mode or exclusive mode) on each object in the database 
        - Read: acquire the lock in shared mode (allow several transactions to hold it), but transaction must wait for an exclusive lock
        - Write: acquire the lock in exclusive mode (only 1 transaction can hold it, others must wait)
        - First read then write: upgrade its shared lock to an exclusive lock
    - First phase: acquire lock; second phase: release lock.
    - Performance is poor, deadlock may happen

    - **Predicate lock**: belongs to all objects that match some search condition
        - Read for some condition: acquire a shared-mode predicate lock on the conditions of the query, if another transaction has an exclusive lock on the objects matching the conditions, then the current transaction must wait
        - Write: first check whether either the old or the new value matches any existing predicate lock, if there is matching the current transaction must wait

    - **Index-range lock (next-key locking)**: 
        - Similar to predicate locks, but is based on indices of the rows for the search condition
        - Better performance but may lock a bigger range of objects
        - If there is no suitable index where a range lock can be attached, the database can fall back to a shared lock on the entire table

- Optimistic concurrency control techniques such as **Serializable Snapshot Isolation (SSI)**
    - ***optimistic*** concurrency control mechanism: instead of blocking if something may go wrong, transactions continue anyway 
    - all reads within a transaction are made from a consistent snapshot of the database
    - when a transaction wants to commit, database checks whether isolation was violated (a query result might have changed), and if so the transaction is aborted and has to be retried
    - By avoiding unnecessary aborts, SSI preserves snapshot isolation’s support for long-running reads from a consistent snapshot.
    - How database checks whether isolation was violated
        - Detecting stale MVCC reads (uncommitted write occurred before the read due to visibility rules)
            - When the transaction wants to commit, the database checks whether any of the ignored writes have now been committed. If so, the transaction must be aborted.
        - Detecting writes that affect prior reads (the write occurs after the read)
            - Similar to the index-range locks, index is recorded for the transaction when reading; when writing, the index will be checked and notify the transaction to abort
    - Performance:
        - one trade-off is the granularity at which transactions’ reads and writes are tracked
        - Compared to two-phase locking, the big advantage is that one transaction doesn’t need to block waiting for locks held by another transaction.


## Reference:

- [Designing Data-Intensive Applications](https://www.amazon.ca/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321/ref=sr_1_1?dchild=1&gclid=Cj0KCQjw_8mHBhClARIsABfFgpg5q5IQvE2s5OBULx6LQFDETV41haS67EE3JAfvobPADJUJHN7dUbsaAjjrEALw_wcB&hvadid=285888202784&hvdev=c&hvlocphy=9001327&hvnetw=g&hvqmt=e&hvrand=12070511852976413586&hvtargid=kwd-407664346480&hydadcr=16109_9598899&keywords=design+data+intensive+application&qid=1626587742&sr=8-1)
