**Why Is Statelessness Important in REST?**
Statelessness means the server does not store any client session information. Every request must contain all necessary data.

- scalability , simplicity, reliability, performance in distributed system.

**_It makes REST APIs easier to scale horizontally._**

---

**Common HTTP Status Codes in REST APIs**

- 200 – OK (Successful GET or PUT)
- 201 – Created (Resource successfully created)
- 204 – No Content (Successful request with no response body)
- 400 – Bad Request (Client error)
- 401 – Unauthorized (Authentication required)
- 403 – Forbidden (Access denied)
- 404 – Not Found (Resource not found)
- 500 – Internal Server Error (Server-side issue)

---

**Limitations of REST APIs**

- Over-fetching and under-fetching of data
- No built-in real-time support
- Multiple endpoints may be needed for complex data
- Statelessness may increase repeated data transfer
- Less flexible compared to GraphQL in some cases

---

**How does REST differ from GraphQL?**
REST and GraphQL are both used for building APIs, but they differ in how data is requested and structured.

**_In REST:_**

- We have multiple endpoints (like /users, /posts)
- The server decides the structure of the response
- It can cause over-fetching or under-fetching of data

**_In GraphQL:_**

- There is usually a single endpoint
- The client decides exactly what data it needs
- It prevents over-fetching and under-fetching

REST is simpler and widely adopted, while GraphQL gives more flexibility and efficiency for complex applications.

---

**What is idempotency in REST?**
Idempotency means that making the same request multiple times produces the same result as making it once.

---

**What problems can arise if REST is not truly stateless?**

- It becomes harder to scale
- Load balancing becomes difficult
- Server memory usage increases
- Sessions must be maintained
- Failures can affect user sessions
- It reduces reliability in distributed systems

---

**Database sharding and replication**
**_Replication :_** Copy same database to multiple servers.

- purpose : high availability, read scaling.

**_Sharding :_** Split data across multiple databases.

- purpose : Handle huge data volume

|            | Replication       | Sharding        |
| ---------- | ----------------- | --------------- |
| Purpose    | High availability | Scale data      |
| Data       | Same copy         | Different parts |
| Complexity | Medium            | High            |

---
