##### what is client and server?

> Client : The client is the user’s device or browser that sends requests and shows information

> Server : The server is the computer that stores data and handles requests from clients. It sends back the needed information or files.

> In shorts : The client asks, and the server provides.

##### What is REST and how does it work?

> REST (Representational State Transfer) is a set of rules for building APIs that use HTTP methods to access and modify data.

##### Difference between HTTP and HTTPS?

> HTTP sends data openly, while HTTPS sends data securely (encrypted) so no one can steal or change it. HTTP uses port 80 while HTTPS uses 443.

#### what is webhook?

> A webhook is a way for one system (application or server) to automatically send real-time data or updates to another system when a specific event happens. A webhook is like a notification system for apps — when something happens, one app calls another app by sending it data instantly.

#### How nodejs handle concurrency ?

> Node.js handles concurrency using an event-driven, non-blocking I/O model built around the event loop, not threads

#### What are middleware ?

> Types of Middleware
>
> - Application-level middleware : Registered directly on the app object.
> - Route-level middleware : Runs only for specific routes.
> - Built-in middleware
> - Error-handling middleware (special 4-argument signature)

#### What is authentication and authorization ?

> Authentication = verify who the user is. Authorization = verify what the user can access

> Types of authentication ->
>
> - Token-based auth (JWT) — stateless : No session stored on the backend
> - Session based auth - stateful : Server store user session (in memory or DB)

| Authentication Type | Stateful/Stateless | Use Case                         |
| ------------------- | ------------------ | -------------------------------- |
| Session Cookies     | Stateful           | Websites, dashboards             |
| JWT                 | Stateless          | APIs, mobile apps, microservices |
| OAuth 2.0           | Either             | Social login, API access         |
| SSO                 | Stateful           | Enterprise systems               |
| API Keys            | Stateless          | Third-party APIs                 |
| HMAC                | Stateless          | Webhooks, secure APIs            |
| Basic Auth          | Stateless          | Simple internal tools            |
| Magic Links         | Stateless          | Passwordless login               |
| OTP / TOTP          | Stateless          | High security apps               |

#### Types of Authorization.

| **Authorization Type**                       | **Meaning / Definition**                                                    | **Where It's Used**                                              | **Explanation (Easy to Understand)**                                                                                                              |
| -------------------------------------------- | --------------------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **RBAC (Role-Based Access Control)**         | Access is granted based on a user's **role**                                | Admin dashboards, SaaS apps, CMS systems                         | You create roles (Admin, Manager, User) → Each role has permissions. Users inherit permissions from their role. Simple and scalable.              |
| **PBAC (Permission-Based Access Control)**   | Access is based on **individual permissions** instead of roles              | When fine control is needed (e.g., each action has a permission) | Instead of “Admin,” you define permissions like `read:user`, `edit:post`, `delete:order`. Very flexible but harder to manage.                     |
| **ABAC (Attribute-Based Access Control)**    | Access based on **attributes** of user, resource, and environment           | Enterprise systems, banking, healthcare                          | Rules look like: “User’s department must match document's department” or “only allow access if request comes from office network.” Very powerful. |
| **RLS (Row-Level Security)**                 | Users can access **only the specific rows** they own or are allowed to view | Databases (PostgreSQL RLS), Supabase, Hasura                     | Useful when you want: “User can only see their own records.” Rules are applied at the database level.                                             |
| **Field-Level Authorization**                | User can access only **specific fields/columns** of a record                | APIs, GraphQL, sensitive data filtering                          | Example: A regular user can't see `salary` or `emailVerified` field, but an admin can. Ensures sensitive attributes stay protected.               |
| **Scope-Based Authorization (OAuth Scopes)** | Tokens define **scopes**, limiting what the user/app can access             | Google OAuth, GitHub OAuth, API integrations                     | Example: A token may have `drive.readonly` or `calendar.write`. An app can only do what the scope allows. Ideal for API permissions.              |
| **Context-Based Authorization**              | Access based on **real-time context** (device, IP, session time)            | Security-sensitive apps, banking apps                            | Example: Allow action only if the request is from a trusted device or during business hours. Often combined with ABAC.                            |
| **MAC (Mandatory Access Control)**           | System decides access rules; users **cannot override**                      | Military, government, extremely secure systems                   | Everything is classified: Public, Confidential, Secret, Top Secret. Users can only access levels they are cleared for.                            |
| **DAC (Discretionary Access Control)**       | Data owners decide who gets access                                          | File systems, collaborative platforms                            | Example: A user can share their file with others — permission is controlled by the resource owner.                                                |

_Simple_

| Type        | Simple Meaning                             |
| ----------- | ------------------------------------------ |
| RBAC        | User gets access based on **Role**         |
| PBAC        | User gets access based on **Permissions**  |
| ABAC        | Access uses **attributes & rules**         |
| RLS         | User can only see **their own rows**       |
| Field-Level | User can see **only certain fields**       |
| Scope-Based | Token defines **what actions are allowed** |
| MAC         | System-enforced strict rules               |
| DAC         | Resource owner sets access                 |

#### What is rate limiting ?

> Rate Limiting is a backend technique used to control how many requests a client can make to a server within a specific time period. RL helps to Prevent DDoS attacks.

##### Types of rate limiting

> Fixed Window (Window Counter) : Time is divided into fixed windows (e.g., every 1 minute), Each request increments a counter in that window, When limit is reached → block.

> Sliding Window Log : Stores a timestamp for each request, Removes timestamps older than time window, Count remaining timestamps.

> Sliding Window Counter (Hybrid) : Stores request count in smaller time slices,Combines nearby slices to approximate usage.

> Token Bucket (Most Common) : Bucket has tokens (e.g., 100 tokens), Every request consumes 1 token, Tokens refill at a fixed rate.

> Leaky Bucket : Requests enter a queue (bucket), Requests leave bucket at a constant rate (like water leaking).

> ##### Which type is MOST used in real backend systems? --- Token Bucket + Redis is the industry standard

#### How Redis is used for rate limiting?

> Redis is perfect for rate limiting because it is:
>
> - In-memory (very fast)
> - Supports atomic operations (safe for concurrency)
> - Can expire keys automatically
> - Works across distributed servers

> **APPROACH** - We store request count or token count in Redis, Each request updates the value, Redis automatically resets (via TTL), If the user hits the limit → reject.

#### What is encryption and decryption ?

> **Encryption** - Converting plain data into unreadable format (ciphertext) using a key.
> **Decryption** - Converting encrypted data back to its original form using a key.
>
> **Types of Encryption**
>
> - **Symmetric Encryption** : Same key is used for encrypting and decrypting. Fast and efficient. Example algorithms: AES, DES, ChaCha20

> - **Asymmetric Encryption (Public/Private Key)** : Uses public key to encrypt, private key to decrypt. Slower, but more secure for sharing keys. Example algorithms: RSA, ECC

> - **Password Hashing (One-way Encryption)** : Passwords should never be stored in plain text. Hashing is one-way (cannot decrypt). Use libraries like bcrypt, argon2.

> - **Encryption in Transit** : Use HTTPS/TLS to encrypt data between client and server.

##### Best Practices

**Use AES-256 for symmetric encryption.**

**Use RSA/ECC for asymmetric encryption.**

**Never store plain passwords; use bcrypt/argon2.**

**Store keys securely (env vars, secret manager).**

**Use HTTPS for all client-server communication.**

**Always use proper IVs (initialization vectors) for symmetric encryption.**

#### What is JWT ?

> JWT is a token-based authentication method. It creates a signed token that the server gives to the client after login. The client sends that token in every request to prove identity.

#### What is a Queue (Message Queue)?

A Queue is a system that allows you to process tasks asynchronously (in the background).
Instead of doing everything instantly, tasks are pushed into a queue and processed slowly or by workers. We use queues to handle heavy or slow tasks, To prevent server overload, To decouple systems.

**Popular Queue Systems**

- RabbitMQ

- Kafka

- Redis Queue (Bull, BullMQ)

- Amazon SQS

- Google Pub/Sub

#### **JWT vs OAuth vs Sessions**

| Feature  | **JWT**                    | **OAuth**               | **Sessions**                |
| -------- | -------------------------- | ----------------------- | --------------------------- |
| Type     | Token format               | Authorization framework | Server-based authentication |
| State    | Stateless                  | Stateless               | Stateful                    |
| Storage  | Client                     | OAuth provider          | Server                      |
| Use Case | APIs, microservices        | Third-party access      | Traditional web apps        |
| Security | Medium (needs precautions) | High                    | High                        |
| Logout   | Hard (token still valid)   | Built-in                | Easy                        |

#### Refresh Token Flow (Access Token + Refresh Token System)

Refresh Token Flow is used to keep users logged in securely without asking them to log in again when the access token expires.

> - Why do we need Refresh Tokens?
>   Because: Access tokens expire quickly (like 15 minutes). If a hacker steals an access token, it becomes useless after a short time. Requiring the user to log in again every 15 minutes is bad UX. So we use: Short-lived access token → protects security, Long-lived refresh token → keeps user logged in

**How Refresh Token Flow Works (Step-by-Step)**
- step 1 :- User logs in : User sends email & password, Server verifies and returns: access token and refresh token.

- step 2 :- Client stores tokens : Access Token → memory / localStorage & Refresh Token → HTTP-only cookie (most secure)

- step 3 :- Client uses Access Token : Client uses Access Token

- step 4 :- Access Token expires 
> User tries a new request… sever respond with 401 - unauthorized

- step 5 :- Client sends Refresh Token automatically : Server verifies refresh token.

- step 6 : Server returns a NEW Access Token
