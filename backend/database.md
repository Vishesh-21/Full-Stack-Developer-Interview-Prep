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

