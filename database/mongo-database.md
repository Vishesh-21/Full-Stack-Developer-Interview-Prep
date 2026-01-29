**MongoDB was first introduced (released) in 2009 as an open-source database. Its development started earlier around 2007 before that release.**

**Facebook mainly uses MySQL (with its own optimized engine like MyRocks).It also uses NoSQL databases like Cassandra and HBase for large-scale data, and TAO for graph data (friends, relationships).**

---

**If SQL (MySQL) can already do the job, why do we need NoSQL databases like MongoDB?**
they both solve different problems :

- how sql works ?
  - relational
  - schema based
  - strong relationship and consistency
  - prefect for banking system, payments, erp, auth systems
    **Problem** : When applications grow very large:
  - Joins become expensive
  - Schema changes are painful
  - Horizontal scaling is hard
  - Data shape is not always predictable

- why nosql exists?
  - Flexible schema
  - High read/write throughput
    **when to use**
  - Nested or JSON-like data
  - Data structure changes frequently
  - High traffic & scalability
  - Read-heavy systems
  - Microservices

| MySQL              | MongoDB                 |
| ------------------ | ----------------------- |
| Relational (SQL)   | NoSQL (Document-based)  |
| Fixed schema       | Flexible schema         |
| Tables & rows      | Collections & documents |
| Uses JOINs         | Embedded data           |
| Strong consistency | High scalability        |

---

**CAP theorem **

CAP theorem says:In a distributed system, you can choose only 2 out of 3.

- Consistency : All users see the same data at the same time.
- Availability : System always responds, even if data is not perfect.
- Partition Tolerance : System works even if some servers fail or network breaks.

| Database      | CAP Choice           |
| ------------- | -------------------- |
| MySQL         | C + A                |
| MongoDB       | C + P (configurable) |
| Cassandra     | A + P                |
| Redis Cluster | A + P                |

> MongoDB document limit = 16MB

**Redis is used for :** cache, session, rate limiting, counters, queues.

**Can NoSQL databases handle transactions?**
Yes, some NoSQL databases like MongoDB now support multi-document transactions, but SQL databases provide stronger and more mature ACID guarantees.
For critical financial operations, SQL is preferred.

**What is eventual consistency?**
In distributed NoSQL databases, not all nodes see the same data immediately.
The system eventually becomes consistent.

**What is sharding in MongoDB?**
Sharding is horizontal scaling — splitting data across multiple servers (shards) to handle large datasets.
Helps improve read/write throughput and scalability.
Example: Social media posts split by user ID across servers.

**Can SQL scale horizontally?**
Yes, but with more complexity:

- Read replicas for scaling reads
- Sharding or distributed SQL for writes
- Still harder than NoSQL for massive, dynamic datasets

**How do you index in MongoDB vs SQL?**

- SQL: B-tree indexes on columns
- MongoDB: single-field, compound, text, geo indexes

**Explain denormalization in NoSQL**
Store redundant data in one document to avoid joins and improve read performance.
Trade-off: write/update operations may be heavier.

**Is NoSQL faster than SQL?**
Depends on use case.

- NoSQL: fast for document reads/writes, horizontal scale

- SQL: fast for joins, transactions, structured queries

**When does MongoDB fail badly?**

- Transaction-heavy apps
- Uncontrolled schema
- Very large documents (>16MB)
- Complex relational queries

**Explain ACID vs BASE**

- SQL → ACID (Atomic, Consistent, Isolated, Durable)
- NoSQL → BASE (Basically Available, Soft state, Eventually consistent)

**Why don’t we just horizontally scale MySQL always?**
Fact: MySQL (and most SQL databases) can scale horizontally, but it’s harder than NoSQL.

**Challenges**

- Joins across shards are complex : SQL is relational, often requires joins.If you shard tables across multiple servers, joins become very slow or impossible.

- Transactions across shards are difficult : ACID guarantees are easy on a single server.Across multiple servers, maintaining atomicity and consistency is hard.

- Schema changes are harder : Adding columns or changing schema across multiple shards → error-prone.

- Replication vs Sharding : SQL uses replication for scaling reads → good for read-heavy apps. Write scaling → needs sharding, which requires careful planning.

---

**What is replication in NoSQL databases**?

- Replication = copying data across multiple nodes for high availability
- MongoDB: primary node + secondary nodes
- Changes on primary automatically propagate to secondaries
- Provides fault tolerance and read scalability

---

**How does MongoDB handle joins (lookup)?**

- mongoDB does not have traditional SQL joins, but $lookup simulates joins
- performs left outer join between collections
