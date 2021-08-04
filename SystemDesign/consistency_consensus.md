# Consistency and Consensus

## Linearizability

- Imagine each operation (read or write) is marked with a vertical line at the time of execution, the requirement of linearizability is that the lines joining up the operation markers always move forward in time, never backward
    - once a new value has been written or read, all subsequent reads see the value that was
    - it doesn’t assume any transaction isolation: another client may change a value at any time
- essentially means “behave as though there is only a single copy of the data, and all operations on it are atomic”
- Used for leader election in coordination service (such as Zookeeper)
- Used for uniqueness constraints in database

### Linearizability vs Serializability

- Serializability
    - an isolation property of transactions
    - It guarantees that transactions behave the same as if they had executed in some serial order
    - It is okay for that serial order to be different from the order in which transactions were actually run
- Linearizability
    - a recency guarantee on reads and writes of a register (object)
    - It doesn’t group operations together into transactions, so it does not prevent problems such as write skew

## CAP theorem

- **CAP (Consistency, Availability, Partition tolerance) theorem**: you can only pick 2 out of 3
- A better way to describe is **either Consistent or Available when Partitioned**

## Ordering Guarantees

- *causal dependency*: i.e. question and the answer, git commit history and brunches
- *consistent with causality*: the effects of all operations that happened causally before that point in time are visible, but no operations that happened causally afterward can be seen.
    - For example, if the snapshot contains an answer, it must also contain the question being answered
- *causally consistent*: system obeys the ordering imposed by causality
- A *total order* always allows any two elements to be compared (i.e. unique sequence number)
- *partially ordered*: in some cases one set is greater than another, but in other cases they are incomparable.
- Tracking causal dependency: 
    - Explicitly tracking all the data that has been read would mean a large overhead.
    - a better way could be to use sequence numbers or timestamps to order events
    - **Lamport timestamp**: a simple method for generating sequence numbers that is consistent with causality
        - Each node has a unique identifier, and each node keeps a counter of the number of operations it has processed
        - The Lamport timestamp is then simply a pair of (counter, node ID)
        - Lamport timestamp bears no relationship to a physical time-of-day clock, but it provides total ordering
- Total Order Broadcast: protocol for exchanging messages between nodes
    - two safety properties should always be satisfied
        - *Reliable delivery*: No messages are lost: if a message is delivered to one node, it is delivered to all nodes.
        - *Totally ordered delivery*: Messages are delivered to every node in the same order.
    - Implementation:
        - assume that every time the lock server grants a lock or lease, it also returns a **fencing token**, which is a number that increases every time a lock is granted
        - every time a client sends a write request to the storage service, it must include its current fencing token
        - For example, if a node has delivered message 4 and receives an incoming message with a sequence number of 6, it knows that it must wait for message 5 before it can deliver message 6.
    - Usages: 
        - Consensus services (i.e. Zookeeper)
        - Logs (replication log, transaction log, or write-ahead log)


## Consensus: get several nodes to agree on something

### Two-Phase Commit (2PC)：transaction commit across multiple nodes

- with help of ***transaction manager (coordinator)***, *participants* (nodes that participates in read/write for the transaction) 
- Phase 1: coordinator sends prepare request to each participants, ask if they are able to commit.
- Phase 2: if all are good to commit, commit is performed. Otherwise abort.
- process:
    1. When the application wants to begin a distributed transaction, it requests a **globally unique transaction ID** from the coordinator 
    2. The application begins a single-node transaction on each of the participants, and attaches the globally unique transaction ID to the single-node transaction. All reads/writes are done in one of these node atomically
    3. When the application is ready to commit, the coordinator sends a prepare request to all participants with the global transaction ID. If any one failed, the coordinator sends an abort request for that transaction ID to all participants.
    4. When a participant receives the prepare request, it makes sure that it can definitely commit the transaction under all circumstances. The participant will not abort the transaction, but without actually committing it.
    5. Once the coordinator’s decision has been written to disk, the commit or abort request is sent to all participants. If this request fails or times out, the coordinator must retry forever until it succeeds.
- two crucial “points of no return” (ensure the atomicity of 2PC):
    1. when a participant votes “yes,” it promises that it will definitely be able to commit later (although the coordinator may still choose to abort)
    2. once the coordinator decides, that decision is irrevocable
- coordinator failed
    - The only way 2PC can complete is by waiting for the coordinator to recover. 
    - This is why the coordinator must write its commit or abort decision to a transaction log on disk before sending commit or abort requests to participants
    - when the coordinator recovers, it determines the status of all in-doubt transactions by reading its transaction log. 
    - Any transactions that don’t have a commit record in the coordinator’s log are aborted. 
    - Thus, the commit point of 2PC comes down to a regular single-node atomic commit on the coordinator.
- 2PC is thus called a ***blocking atomic commit protocol***
- ***Three-phase commit (3PC)*** is called ***nonblocking atomic commit*** and requires a ***perfect failure detector*** to ensure nonblocking


### Exactly-once message processing

- implemented by atomically committing the message acknowledgment and the database writes in a single transaction
- If either the message delivery or the database transaction fails, both are aborted, so it can safely be retried later
- all systems affected by the transaction are required to use the same atomic commit protocol


### XA (eXtended Architecture) transactions

- XA is not a network protocol but merely a C API for interfacing with a transaction coordinator
- XA assumes that your application uses a network driver or client library to communicate with the participant databases or messaging services
- The standard does not specify how it should be implemented, but in practice the coordinator is often a library that is loaded into the **same process** as the application issuing the transaction
    - It keeps track of the participants in a transaction, collects their responses after asking them to prepare (via a callback into the driver), and uses a log on the local disk to keep track of the commit/abort decision for each transaction.
    - If the application process crashes, the coordinator goes with it. Since logs are on application server's local disk, the server must be restarted. 
    - The database server cannot contact the coordinator directly, since all communication must go via its client library.
- If the logs are corrupted so that the in-doubt transactions cannot decide the outcome, only manual intervene (by admin) can resolve it, otherwise it'll lock forever
    - one solution: ***heuristic decisions***: allowing a participant to unilaterally decide to abort or commit an in-doubt transaction without a definitive decision from the coordinator, but this MAY break atomicity. Thus, it is only intended only for getting out of catastrophic situations, and not for regular use.
- Limitations:
    - Coordinator can become a single point of failure
    - when the coordinator is part of a **stateless** application server, it changes the nature of the deployment, since the coordinator’s logs become a crucial part, the server is no longer stateless
    - Compatibility: XA cannot detect deadlocks across different systems (since that would require a standardized protocol for systems to exchange information on the locks that each transaction is waiting for), and it does not work with SSI, since that would require a protocol for across different systems.

### fault tolerance consensus

- a fault tolerance consensus algorithm must satisfy the following properties:

    - Uniform agreement: No two nodes decide differently.
    - Integrity: No node decides twice.
    - Validity: If a node decides value v, then v was proposed by some node.
    - Termination: Every node that does not crash eventually decides some value.
        - The system model of consensus assumes that when a node “crashes,” it suddenly disappears and never comes back.
        - any consensus algorithm requires at least a majority of nodes to be functioning correctly in order to assure termination. That majority can safely form a quorum.
- The best-known fault-tolerant consensus algorithms are Viewstamped Replication (VSR), Paxos, Raft, and Zab.

- ***epoch number***: a number such that within each epoch, the leader is unique
    - each time the leader is dead, nodes will start a vote to elect a new leader
    - the election is given an incremented epoch number (totally ordered)
    - if there is conflict, the leader with higher epoch number wins
    - before the selected leader does anything, need to make sure there is no leader with higher epoch number: collect votes from a quorum of nodes
    - so there will be two rounds of voting for the process, one is to select leader, one is to vote on the leader's proposal. If the results of two votes are inconsistent, leader cannot be promoted 

- Limitations of consensus
    - The process by which nodes vote on proposals before they are decided is a kind of synchronous replication, some committed data can potentially be lost on failover
    - Consensus systems always require a strict majority to operate (you need at least 3 nodes)
    - Most consensus algorithms assume a fixed set of nodes that participate in voting, so it's difficult to scale
    - Consensus systems generally rely on timeouts to detect failed nodes


## Reference:

- [Designing Data-Intensive Applications](https://www.amazon.ca/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321/ref=sr_1_1?dchild=1&gclid=Cj0KCQjw_8mHBhClARIsABfFgpg5q5IQvE2s5OBULx6LQFDETV41haS67EE3JAfvobPADJUJHN7dUbsaAjjrEALw_wcB&hvadid=285888202784&hvdev=c&hvlocphy=9001327&hvnetw=g&hvqmt=e&hvrand=12070511852976413586&hvtargid=kwd-407664346480&hydadcr=16109_9598899&keywords=design+data+intensive+application&qid=1626587742&sr=8-1)
