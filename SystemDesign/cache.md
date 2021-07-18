# Cache

When talking about cache, here we are talking about web development related cache. 

[Here is a good article to start with](https://www.digitalocean.com/community/tutorials/web-caching-basics-terminology-http-headers-and-caching-strategies)

Here we are focusing on database cache.

- Cache Usage Pattern
    - **Cache Aside**: application is responsible for reading and writing from the database and the cache doesn't interact with the database at all
        - Application queries data from cache first
        - if cache contains data return directly bypasses database
        - if not fetch from database, then stores in cache
        - The most common cache-aside systems are Memcached and Redis
    - **Cache-as-SoR (system-of-record)**: the application treats cache as the main data store and reads data from it and writes data to it
        - **Read through**
            - the cache is configured with a loader component that knows how to load data from the database
            - if an entry does not exist within the cache, the cache invokes the loader to retrieve the value from the database, then caches the value, then returns it to the caller.
        - **Write through**
            - the cache is configured with a writer component that knows how to write data to database
            - When the cache is asked to store a value for a key, the cache invokes the writer to store the value in the SoR, as well as updating the cache.
        - **Write behind**
            - Similar to write behind, rather than writing to the database while the thread making the update waits (as with write-through), write-behind queues the data for writing at a later time.
- Cache Eviction Policies
    - LRU: least recently used
    - LFU: least frequently used
    - FIFO: first in first out
    - LIFO: last in first out
    - FILO: first in last out
    - and many many more


## Redis 

### Memory management 

- Redis only caches all the key information. Not all data storage occurs in memory
- When the physical memory is full, Redis may swap values not used for a long time to the disk.
- When the memory usage exceeds the threshold value, Redis will trigger the swap operation.
- Redis calculates the values for the keys to be swapped to the disk based on *“swappability = age\*log(size_in_memory)”* 
- The machine memory must keep all the keys and it will not swap all the data.
- When Redis swaps the in-memory data to the disk, the main thread that provides services, and the child thread for the swap operation will share this part of memory.
    - So, if you update the data you intend to swap, Redis will block this operation, preventing the execution of such a change until the child thread completes the swap operation.

### Multi-threading

- Redis was known to be single threaded, but now its changed
- After Redis 4.0, it also has background threads to process slow operations such as clean up, releasing useless connections, bulk delete, etc
- Redis 6.0 version supporting multi-threading was finally released on 2020-05-02
    - There are two main directions for optimization:
        - To improve network IO performance, typical implementations such as using DPDK to replace the kernel network stack.
        - Use multi-threading to make full use of multi-core, typical implementations such as Memcached.



## Redis vs. Memcached: In-Memory Data Storage Systems

| Comparison | Redis | Memcached |
| :---: | :--------: | :---: |
| Data Types Supported | string, hash, list, set, sorted set | Hash Table with string and integers |
| Server-end data operations | owns more data structures and supports richer data operations | need to copy the data to the client end for similar changes and then set the data back thus increases IO counts and data sizes |
| Memory Management | Encapsulated malloc/free | Slab Allocation mechanism |
| Memory use efficiency | Lower | higher memory utilization rate |
| Data Persistence | RDB snapshot and AOF log | None |
| Performance | single core so higher performance in small data storage | multiple cores so outperforms for storing data of 100k or above |


Reference:

- [Caching for Resiliency](https://medium.com/the-cloud-architect/patterns-for-resilient-architecture-part-4-85afa66d6341#:~:text=There%20are%20two%20basic%20caching,%E2%80%94%20also%20called%20inline%2Dcache.)
- [Database Caching](https://aws.amazon.com/caching/database-caching/)
- [Cache Usage Patterns](https://www.ehcache.org/documentation/3.3/caching-patterns.html)
- [Using Read-Through and Write-Through in Distributed Cache - DZone Database](https://dzone.com/articles/using-read-through-amp-write-through-in-distribute)
- [Cache replacement policies](https://en.wikipedia.org/wiki/Cache_replacement_policies)
- [Redis vs. Memcached: In-Memory Data Storage Systems](https://medium.com/@Alibaba_Cloud/redis-vs-memcached-in-memory-data-storage-systems-3395279b0941)
- [Redis 6.0, which supports multi-threading, is finally released New features serial 13 questions - Programmer Sought](https://www.programmersought.com/article/30635498543/)
