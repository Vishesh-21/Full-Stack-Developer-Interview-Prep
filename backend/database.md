#### SQL and NoSQL

**SQL = Structured, consistent, relational**

- Data fits well into tables

- Follows ACID rules (very safe & reliable)

- Perfect for apps requiring relationships

- Example: banking, ecommerce orders, ERP, accounting

**NoSQL = Flexible, scalable, document-based**

- Data stored as JSON-like objects

- Can store different fields in each document

- Very fast read/write

- Perfect for large scale & real-time apps

- Example: social media posts, chat apps, logs, IoT

#### Why NoSQL database faster than SQL databases?

NoSQL is faster because it stores data as key-value or JSON documents (no joins), scales horizontally across multiple servers, avoids strict ACID rules, uses in-memory caching, and relies on high-performance storage engines optimized for fast read/write operations.

#### Trade-offs in choosing MongoDB over PostgreSQL

**🟩Advantages of MongoDB**

- Flexible schema (JSON)

- Faster for large write-heavy workloads

- Easier horizontal scaling (sharding)

- Great for nested/complex JSON data

- Fewer joins → simpler designs

- Perfect for unstructured or semi-structured data

**🟥 Disadvantages of MongoDB**

- Weaker consistency guarantees (eventual consistency)

- No complex joins like SQL

- No strong transaction support compared to PostgreSQL

- Difficult to maintain integrity because of denormalization

- Query performance can degrade without proper indexes

**🟦 Advantages of PostgreSQL**

- Strong ACID compliance

- Excellent relational modeling

- Supports complex queries & joins

- Better for business logic & analytic queries

- Reliable for financial or mission-critical data

**🟥 Disadvantages of PostgreSQL**-

- Harder to scale horizontally

- Schema changes can be expensive

- Slower for huge unstructured datasets

#### Comparison of postgreSQL and mySQL.

| Feature             | PostgreSQL                     | MySQL                     |
| ------------------- | ------------------------------ | ------------------------- |
| **Focus**           | Advanced features, correctness | Speed, simplicity         |
| **SQL Compliance**  | Very high                      | Moderate                  |
| **JSON**            | Best (JSONB)                   | Good but limited          |
| **Complex Queries** | Excellent                      | Average                   |
| **Performance**     | Better for writes & analytics  | Better for read-heavy     |
| **Extensibility**   | Very high                      | Low                       |
| **Use Cases**       | Finance, analytics, enterprise | Web apps, CMS, e-commerce |

**Cascade Operations** : When a row in a parent table is deleted or updated, rows in a child table that reference the modified row can be automatically deleted or updated. This is managed by foreign key constraints.

**ON DELETE CASCADE**: If a row in the parent table is deleted, all corresponding rows in the child table are also deleted.
**ON UPDATE CASCADE**: If a row in the parent table is updated, the corresponding foreign key values in the child table are also updated.

#### What is the difference between candidate key, super key, and primary key?

- A super key is a set of one or more columns that uniquely identifies each row in a table.

- A candidate key is a minimal super key, meaning it has no unnecessary columns; it is a potential primary key.

- A primary key is a candidate key that has been chosen to uniquely identify rows in a table; it cannot contain NULL values and must be unique.

#### What is normalization? Why is it needed?

Normalization is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing a database into multiple related tables and establishing relationships between them.

**Need of normalization:**

- Eliminate Data Redundancy: Reduces duplicate data storage, saving space
- Improve Data Integrity: Minimizes inconsistencies and anomalies
- Avoid Deletion Anomalies: Prevents unwanted loss of data when deleting records
- Improve Query Performance: Better organized data leads to faster and more efficient queries
- Maintain Data Consistency: Changes are made in one place, affecting all related data

#### What is denormalization?

Denormalization is the process of intentionally introducing redundancy into a normalized database to improve query performance. It's the opposite of normalization.

**Why is it needed?**

- Improve Read Performance: Reduces the number of joins needed for queries
- Simplify Queries: Makes complex queries easier to write and understand
- Optimize for Specific Workloads: Tailors the database structure for common, performance-critical operations
- Reduce Complex Joins: Avoids costly join operations, especially in data warehousing or reporting
- Enhance Reporting: Speeds up data retrieval for analytical and reporting purposes

#### What is the difference between DELETE, TRUNCATE, and DROP commands?

- DELETE: Removes specific rows from a table based on a condition
  **characteristics**

  - Purpose: Removes specific rows from a table based on a condition
  - Slower than TRUNCATE (row-by-row deletion)
  - Generates individual delete statements in the transaction log
  - Can be rolled back if not committed
  - Identity value is not reset - DML Command

- TRUNCATE: Removes all rows from a table quickly
  **characteristics**

  - Faster than DELETE (deallocates data pages)
  - Minimal logging in the transaction log
  - Cannot be rolled back in some databases
  - Identity value is reset - DDL Command
  - Release the space occupied by the table.

- DROP: Deletes the entire table structure and data
  **characteristics**
  - Permanently removes the table and its data
  - Cannot be rolled back
  - All associated indexes, triggers, and constraints are also removed
  - Releases all space occupied by the table - DDL Command

#### What is a join? Explain different types of joins.

A join is used to combine rows from two or more tables based on a related column between them. Joins allow you to retrieve data from multiple tables in a single query.

- Retrieve related data from multiple tables
- Avoid data redundancy
- Organize data in normalized form across tables
- Create meaningful relationships between tables

**Types of joins:**

- INNER JOIN: Returns records with matching values in both tables.
- LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table.
- RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table.
- FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table.
- CROSS JOIN: Returns the Cartesian product of the joined tables.

#### What is a self-join?

A self-join is a join where a table is joined with itself. used when : Data in the same table needs comparison

#### What are indexes in DBMS? Why are they used?

Indexes are data structures that improve the speed of data retrieval operations on a database table at the cost of additional storage space and slower write operations. They are used to quickly locate and access the data without having to scan the entire table.

**Why are they used?**

- Faster Data Retrieval: Significantly speeds up SELECT queries.
- Unique Constraints: Enforce uniqueness on one or more columns.
- Primary Keys: Automatically create a unique index on the primary key.
- Foreign Keys: Can improve performance of joins involving foreign keys.
- Sorting and Grouping: Can make ORDER BY and GROUP BY operations faster.

| Clustered Index        | Non-Clustered Index       |
| ---------------------- | ------------------------- |
| Physically sorts data  | Does not sort actual data |
| Only one per table     | Multiple allowed          |
| Faster retrieval       | Slightly slower           |
| Primary key by default | Secondary indexes         |

#### What is the difference between clustered and non-clustered index?

| Clustered Index        | Non-Clustered Index       |
| ---------------------- | ------------------------- |
| Physically sorts data  | Does not sort actual data |
| Only one per table     | Multiple allowed          |
| Faster retrieval       | Slightly slower           |
| Primary key by default | Secondary indexes         |

#### What are views in SQL?

A view is a virtual table in SQL that is based on the result set of a SELECT query. It does not store data itself but provides a way to present data from one or more tables in a specific format or structure.

**Characteristics**

- Simplicity : Hide complex queries behind simple view names
- Data Abstraction: Hide implementation details from users
- Security: Restrict access to specific columns or rows
- Consistency: Ensure everyone uses the same data logic
- Reusability: Use the same view in multiple queries

**Disadvantages**

- Performance: Views with complex queries can be slow
- Updatability: Not all views can be updated
- Maintenance: Modifying underlying tables affects views
- Storage: Data not stored (must be computed on query)

**Note : Materialized views store the actual data and update periodically, improving performance.**

#### Difference between having clause and where clause?

| WHERE                          | HAVING                   |
| ------------------------------ | ------------------------ |
| Filters rows                   | Filters groups           |
| Used before GROUP BY           | Used after GROUP BY      |
| Cannot use aggregate functions | Uses aggregate functions |

#### Difference between UNION and UNION ALL?

**UNION** : Combines results from two or more SELECT queries and removes duplicate rows.

**UNION ALL** : Combines results from two or more SELECT queries and keeps all rows, including duplicates.

| UNION              | UNION ALL        |
| ------------------ | ---------------- |
| Removes duplicates | Keeps duplicates |
| Slower             | Faster           |
| Performs sorting   | No sorting       |

#### What is a transaction in DBMS?

A transaction is a sequence of one or more SQL operations (INSERT, UPDATE, DELETE, SELECT) that are executed as a single unit. All operations in a transaction either complete successfully or all fail together.

**Characteristics**

- Atomicity : All operations succeed or none do
- Consistency : Database remains in a valid state
- Isolation : Transactions do not interfere
- Durability : Changes are permanent once committed

**Transaction States**
START TRANSACTION
↓
EXECUTE STATEMENTS
↓
COMMIT (Success) OR ROLLBACK (Failure)
↓
END TRANSACTION

```sql
BEGIN TRANSACTION;
    -- Atomicity: All steps succeed or fail together

    -- Check balance (Consistency: valid state)
    SELECT Balance FROM Accounts WHERE CardID = '1234';

    -- Deduct amount (Isolation: no interference)
    UPDATE Accounts SET Balance = Balance - 100 WHERE CardID = '1234';

    -- Dispense cash
    UPDATE ATMCash SET Amount = Amount - 100 WHERE ATM_ID = 'ATM001';

    -- Log transaction
    INSERT INTO Transactions VALUES ('Withdrawal', 100);

COMMIT;
-- Durability: Amount withdrawn is permanently recorded
```
