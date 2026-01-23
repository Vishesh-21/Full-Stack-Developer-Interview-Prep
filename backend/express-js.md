**Express.js :** Express.js is a minimal and flexible Node.js web application framework used to build web applications and RESTful APIs. It simplifies handling HTTP requests, routing, middleware, and responses.

- Why is Express.js used?
  - Simplifies server-side development
  - Fast and lightweight, easy routing system, support middleware
  - ideal for REST api's

**Middleware :** Middleware is a function that executes between the request and the response. It can: Modify request/response objects, End the request-response cycle, call the next middleware. Middleware executes top-to-bottom

**routing :** Routing defines how an application responds to specific HTTP methods and URLs.

**Difference between app.use and app.send**
| app.use() | app.get() |
| -------------------------- | ------------------ |
| Works for all HTTP methods | Works only for GET |
| Used mainly for middleware | Used for routes |
| No specific path required | Requires path |

**Next() :** next() passes control to the next middleware function in the stack.

**Express.Router() :** Express.Router() is a mini express application that helps to organize routes and middleware. Used to create modular and reusable route handlers.

**Difference between app.send , app.render and app.json**
| app.send() | app.render() | app.json() |
| -------------------------------- | ------------------------------------------- | --------------------------------------------------- |
| Sends various HTTP responses | Renders a view template | Sends a JSON response |
| Can send strings, objects, files, and auto detect data type | Sends HTML generated from a template | Automatically sets Content-Type to application/json |
| No template engine needed | Requires a template engine (e.g., Pug, EJS) | Converts JavaScript objects to JSON strings |

**CORS :** CORS (Cross-Origin Resource Sharing) allows or restricts resources from different domains.

**How do you secure an Express application?**

> Use helmet, Validate inputs, Use HTTPS, Handle errors properly, Use authentication & authorization

**MVC architecture :**

- Model : Handles data logic, interacts with the database
- View : Presents data to the user and ui part
- Controller : Handles user input, interacts with model and view

**How does Express.js work internally?**
Express is built on top of Node.js’ http module. Internally:

- Creates an HTTP server using http.createServer()
- Maintains a middleware stack
- Each request flows sequentially through middleware
- Routes are matched using path + HTTP method
- Response is sent once a middleware ends the cycle

**Explain the Express request–response lifecycle**
Client sends HTTP request ➡️ Express receives it via Node HTTP server ➡️ Global middleware executes ➡️ Route-specific middleware executes ➡️ Controller handles logic ➡️ return response ➡️ Error middleware handles failures

**What is the difference between process.nextTick() and setImmediate()**
**process.nextTick()** : schedules a callback to be executed immediately after the current operation, before the event loop continues to the next phase.

- **Characteristics**
  - Executes before I/O callbacks, Runs before setImmediate() and setTimeout()
  - Part of the microtask queue, Can block the event loop if overused

**setImmediate()** : schedules a callback to run in the check phase of the event loop, after I/O events are processed.

- **Characteristics**
  - Executes after I/O callbacks, Uses the macrotask queue
  - Does not block the event loop

| Feature              | process.nextTick()          | setImmediate()             |
| -------------------- | --------------------------- | -------------------------- |
| Queue type           | Microtask queue             | Macrotask queue            |
| Execution timing     | Before event loop continues | After I/O callbacks        |
| Can block event loop | Yes                         | No                         |
| Typical use          | Immediate logic, cleanup    | Non-blocking deferred work |
| Risk                 | Event loop starvation       | Safe for heavy tasks       |

```js
app.get("/", (req, res) => {
  process.nextTick(() => console.log("nextTick"));
  setImmediate(() => console.log("setImmediate"));
  res.send("Hello");
});

> **Execution order :** Route handler runs ➡️ process.nextTick() ➡️ Response sent ➡️ setImmediate()
```

**How do you optimize Express for high traffic?**

- Use cluster mode
- Enable gzip compression
- Use caching (Redis)
- Avoid blocking code
- Use async/await properly
- Limit payload size
- Use reverse proxy (NGINX)

> **Gzip compression** is a lossless data-compression technique used to reduce the size of data transmitted over a network or stored on disk. It is most commonly used in web applications to compress HTTP responses, improving performance and reducing bandwidth usage. file extension .gz and content - encoding(HTTP) : gzip.

> | Feature           | Gzip                | Brotli                 |
> | ----------------- | ------------------- | ---------------------- |
> | Compression ratio | Good                | Better                 |
> | Speed             | Faster              | Slightly slower        |
> | Browser support   | Universal           | Modern browsers        |
> | Use case          | Default safe choice | Best for static assets |

> **NOTE** : Many production setups use Brotli for HTTPS and Gzip as fallback.

> Redis caching optimizes Express applications by reducing database load, improving response time, enabling scalability, and supporting features like session management, rate limiting, and token handling.

**Explain clustering in Express** : Clustering is a way to run multiple Node.js processes to use all CPU cores, since Node.js is single-threaded. It improves performance, scalability, and reliability by distributing requests across worker processes.

**NEED**

- Node.js runs on a single-threaded event loop
- One process can use only one CPU core
- On multi-core machines, this leads to underutilization
- Each worker runs its own Express server.

Clustering solves this by running multiple Node.js processes.

**How Clustering Works**
A master (primary) process is created ➡️ It forks worker processes (usually equal to CPU cores) ➡️ Each worker runs its own event loop ➡️ The OS load-balances incoming requests across workers

**Key Benefits**

- Utilizes all CPU cores, Improves throughput, Increases fault tolerance (worker crashes don’t kill the app), Suitable for CPU-bound tasks

**PM2** : PM2 is a production-grade process manager for Node.js applications. It is used to keep applications running continuously, improve reliability, and enable efficient scaling on single or multi-core systems.

- A daemon-based process manager for Node.js.
- Manages application lifecycle: start, stop, restart, reload
- Provides clustering, monitoring, and zero-downtime deployments
- Commonly used in production environments
- Automatic restarts on crashes

**Difference between Cluster and PM2**

| Feature            | Cluster | PM2      |
| ------------------ | ------- | -------- |
| Built-in           | Yes     | No       |
| Process management | Basic   | Advanced |
| Auto-restart       | Manual  | Yes      |
| Monitoring         | No      | Yes      |

**Idempotency :** Idempotent requests produce the same result on repeated calls. example : get,put but not post.

**What are Express security best practices?**
Use helmet (Helmet helps protect against common web vulnerabilities by setting secure HTTP headers. prevent form : XSS, Clickjacking, MIME-type sniffing etc.), Sanitize inputs, Prevent NoSQL injection, Implement CORS correctly, Use HTTPS, Hide stack traces, Set HTTP headers properly.

**How does Express handle memory leaks?**
Express itself doesn’t manage memory leaks. Developers must:

- Avoid global variables, Clear timers, Close DB connections, Monitor heap usage, Use process.on('exit').

> > Note : **Rate limiting prevent fom brute-force and DDoS attacks**

**Statelessness in Express APIs** : Statelessness means that each API request is independent and contains all the information required to process it. The server does not store client session state between requests. The server does not remember previous requests, Each request is treated as new. Authentication, authorization, and context must be sent with every request

**StateFull in express** : In Express, sessions work by storing user data on the server and sending a unique session ID to the client via a cookie. On each request, the client sends this session ID, allowing the server to retrieve the corresponding session data and maintain user state across requests.

**Cookie-based Authentication vs JWT Authentication**
| Cookie Auth | JWT |
| --------------------- | --------------- |
| Server stores session | Stateless |
| More secure for web | Better for APIs |
| Harder to scale | Easily scalable |

**How do you gracefully shut down an Express server?**
Stop accepting new requests,Finish existing ones, Close DB connections

```js
process.on("SIGTERM", () => server.close());
```

**What is Difference between express and fastify**

- Express is a mature and widely-used Node.js framework, known for its simplicity and huge middleware ecosystem. However, in terms of raw performance, Express is slower compared to Fastify because middleware chaining and sequential processing can introduce overhead.

- Fastify, on the other hand, is designed for high performance. It uses an efficient HTTP router, asynchronous JSON schema validation, and a plugin-based architecture, which allows it to handle more requests per second with lower latency. Benchmarks show that Fastify can be 2–5 times faster than Express for JSON-heavy APIs.

**How does Express differ from NestJS?**
NestJS is a full-featured framework built on Express or Fastify. It offers a modular structure, dependency injection, and built-in features like validation and authentication, making applications more organized, maintainable, and scalable.

**Explain event loop impact on Express**

- Node.js (and Express) is single-threaded and event-driven.
- The event loop lets Express handle multiple requests concurrently without new threads.
- When a request comes in: - It goes to the event queue. - The event loop executes its callback/middleware. - Non-blocking tasks (DB queries, API calls) run in the background. - After completion, the callback is executed by the event loop.
  **Impact** : Blocking code freezes the event loop, delaying other requests.

**Express + redis + jwt architecture with diagram **

- Express.js – Node.js web framework handling API routes and request processing.
- JWT (JSON Web Token) – Used for stateless authentication.
  - Access tokens contain user info and expiry.
  - Refresh tokens are used to get new access tokens.
- Redis – In-memory database used for storing refresh tokens, blacklisting tokens, and session management.
  - Ensures faster lookup than querying a regular database.

> **Flow (Express + Redis + JWT)**
>
> 1. Login: User sends credentials to Express API. Express validates user. Generates access token (short-lived) & refresh token (long-lived). Stores refresh token in Redis. Sends tokens to client.
> 2. API Requests: Client sends access token in request headers. Express verifies token.
> 3. Refresh Token : Client sends refresh token to /refresh-token.Express validates token in Redis. Issues new access token.
> 4. Logout / Token Revocation: Remove or blacklist refresh token in Redis. Access token becomes invalid after expiry.

**Why not store JWT in Redis**

- JWTs are stateless; they contain all info needed for verification.
- Storing JWTs in Redis makes them stateful, adding unnecessary complexity and latency.
- Every request would require a Redis lookup, reducing scalability.
- Valid use cases for Redis: Token revocation / blacklisting, Storing refresh tokens.

> Redis should store refresh tokens, blacklisted access tokens, session metadata, rate limit counters.

**Brute Force Attack :** An attack where an attacker tries many username/password combinations repeatedly to gain unauthorized access.

**DDoS Attack :**An attack where multiple systems flood a server with traffic, making it unavailable to real users.

**Design a notification service (push/email)**

- Separate service for notifications

- Use message queue (RabbitMQ, Kafka)

- Express API triggers messages to the queue

- Worker services consume the queue and send notifications

- Retry logic and failure handling

**Design a scalable chat application**

- Express + WebSocket (Socket.io)

- Redis pub/sub for multiple instances

- Message persistence in DB (MongoDB/Postgres)

- Queueing for offline messages

- Horizontal scaling

**Design a search API**

- Express endpoint with query parameters

- Database indexing and full-text search

- Optional Elasticsearch or Algolia integration

- Pagination and rate limiting

- Caching frequent searches in Redis

**Design a file download service**
Scenario: Serve large files without blocking Express.

- Stream files using res.pipe() or fs.createReadStream
- Avoid reading the whole file into memory
- Rate limiting and authentication
- Use CDN for large-scale delivery


