##### Difference between WHERE and HAVING?

WHERE filters rows before aggregation
HAVING filters groups after aggregation

`Use case: If you need to filter individual records → WHERE. If you need to filter aggregated results (COUNT, SUM) → HAVING.`

##### Types of joins ?

- INNER JOIN → matching records in both tables

- LEFT JOIN → all records from left table + matched from right

- RIGHT JOIN → all records from right table + matched from left

- FULL JOIN → all records from both tables

**Subqueries** : A subquery is a query inside another query.

`Correlated subquery: depends on outer query → runs once per row (slow). Non-correlated subquery: runs once → better performance`

**Note :** Avoid correlated subqueries on large datasets due to performance impact.

**Window Functions :** Window functions perform calculations without collapsing rows.

`Difference from GROUP BY: GROUP BY reduces rows, Window functions preserve rows`

**UNION vs UNION ALL :**

- UNION removes duplicates (slower)
- UNION ALL keeps duplicates (faster)

**What is an Index?**
An index is a data structure that speeds up read operations.
Downside:

- Slows down INSERT, UPDATE, DELETE
- Uses extra storage

**Clustered vs Non-Clustered Index**

- Clustered index → determines physical order of data (only one)
- Non-clustered index → separate structure pointing to data

> Only one clustered index is allowed because data can be stored in only one physical order.

**Composite Index :** An index on multiple columns.

**Optimizing a Slow Query**

- Analyze query logic

- Check indexes

- Use EXPLAIN / execution plan

- Avoid SELECT \*

- Reduce joins and subqueries

- Use proper filtering

**Execution Plan :** Shows how the database executes a query.

#### Transaction & ACID

**Transaction :** A transaction is a set of operations executed as a single unit.

**ACID**

- Atomicity → all or nothing

- Consistency → valid state

- Isolation → independent transactions

- Durability → committed data persists

**Isolation Levels**

- Read Uncommitted - dirty reads, non-repeatable reads, phantom reads
- Read Committed - prevent dirty reads
- Repeatable Read : prevent non-repeatable reads
- Serializable - strongest, prevent phantom reads

> Higher isolation = lower concurrency

**COMMIT vs ROLLBACK**

- COMMIT → save changes
- ROLLBACK → undo changes

If DB crashes mid-transaction → uncommitted changes are rolled back.

#### Normalization & Data Design

**Normalization :** Process of reducing data redundancy.

- 1NF → atomic values
- 2NF → no partial dependency
- 3NF → no transitive dependency

**Denormalization :** Used for performance optimization. Process of increasing data redundancy.
Trade Offs:

- Faster reads
- Data redundancy
- More complex updates

**Primary Key vs Unique Key**

- Primary Key → unique + not null (only one)

- Unique Key → unique but nullable (multiple allowed)

**Cascading :** Cascading in databases refers to automatic actions that propagate changes from a parent table to related child tables when using foreign key constraints.

common types :

- Cascade Delete: Deleting a row in the parent table automatically deletes matching rows in child tables.
- Cascade Update: Updating a key in the parent table automatically updates matching foreign keys in child tables.

**Views :** A virtual table based on a query.

- Normal view → recalculated each time

- Materialized view → stores result physically

**Stored Procedure vs Function**

- Procedure → can modify data, Precompiled SQL logic inside the DB.

- Function → returns value, usually read-only

**Relations :** In relational databases, relations refer to the associations (or relationships) between tables (entities) based on keys (primary and foreign keys). These relationships define how data in one table connects to data in another.

- One-to-One (1:1) : One record in Table A links to exactly one record in Table B, and vice versa.
  Implementation: Foreign key in one table referencing the primary key of the other, with unique constraints.

- One-to-Many (1:N) : One record in Table A links to zero or more records in Table B, but each record in Table B can only link to one record in Table A.

- Many-to-Many (M:N) : Many records in Table A link to zero or more records in Table B, and vice versa.

**CTE(Common Table Expression) :** A CTE is a temporary named result set defined using WITH.

`Why use CTEs:`

- Improves readability

- Can be reused in the same query

- Helpful for recursive queries

**CTE vs Subquery**

CTE → cleaner and easier to debug

Subquery → good for simple one-off logic

**ROW_NUMBER() vs RANK() vs DENSE_RANK()**

- ROW_NUMBER() → unique number per row

- RANK() → same rank for ties, gaps in ranking

- DENSE_RANK() → same rank for ties, no gaps

**EXISTS vs IN**

- IN compares values

- EXISTS checks existence of rows

**Covering Index :** An index that contains all columns needed by the query.

**Index Seek vs Index Scan**

- Index Seek → directly finds rows (fast)

- Index Scan → scans many index pages (slower)

> Seek is preferred due to lower I/O.

**LIKE '%abc' vs LIKE 'abc%'**
Indexes work from the leftmost prefix.

- 'abc%' → index usable

- '%abc' → index cannot be used

**Optimistic vs Pessimistic Locking**

- Optimistic → no locks, check before commit

- Pessimistic → lock data immediately

> Optimistic scales better in read-heavy systems.

**Lock Escalation :** Database converts many small locks into a larger lock.

Problem : Blocks concurrent operations → performance drop.

**Phantom Read :** New rows appear in repeated queries.SERIALIZABLE prevents this by locking the range.

**Surrogate vs Natural Key**

- Natural key → real-world value (email)

- Surrogate key → system-generated ID
  > Surrogate keys are preferred for stability.

**Sharding :** Sharding is a database scaling technique that splits a large database into smaller, more manageable pieces called shards. Each shard contains a subset of the data and is stored on a separate database server (or cluster). This allows the system to handle more data and traffic by distributing the load across multiple servers.

---

#### what is difference between table and view

| Table                    | View                |
| ------------------------ | ------------------- |
| Stores actual data       | Does not store data |
| Occupies storage         | No extra storage    |
| Can be modified directly | Usually read-only   |
| Faster for large data    | Slightly slower     |

---

**Composite key**: A composite key is a primary key made of multiple columns. PRIMARY KEY (order_id, product_id)

---

| Normalization       | Denormalization     |
| ------------------- | ------------------- |
| Less duplicate data | More duplicate data |
| More joins          | Fewer joins         |
| Write optimized     | Read optimized      |

---

**Query Optimization Techniques**

- Use proper indexes
- avoid used of select \*
- use where early : Reduce rows before joins
- optimize joins
- Avoid subqueries when joins are better
- Limit result sets using limit

**Trigger** : A trigger is a SQL code that automatically executes when an event occurs on a table.

**Sharding** : Sharding is splitting data horizontally across multiple databases.

---

**How does SQL handle concurrency?**
SQL handles concurrency using locks and isolation levels.
Lock types:

- Shared (read)
- Exclusive (write)

---


