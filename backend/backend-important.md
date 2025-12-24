**Nginx** : Nginx (pronounced engine-x) is a web server. It helps your website or backend server handle incoming requests from users. Basically use to balancing the load on the server.

`Use of Nginx : `

- Serve Websites (Static Files) : very fast and efficient
- Reverse Proxy : most common use, Nginx sits in front of your backend (Node.js, Python, Java, etc.) and: forward request to backend, receives the response and send it back to the user.
- Load balancing : distribute request evenly, prevent overload, improve uptime.
- SSL/HTTPS handling : Nginx handles HTTPS encryption using SSL certificates (like Let’s Encrypt).
- Caching
- Rate limiting

> Nginx : Fast, efficient server that handles traffic, protects backend, improves performance, and serves files.

---

**Reverse Proxy** : A reverse proxy is a server that sits between the user and your backend server. It receives user requests first, then forwards them to your actual application (Node.js, Python, etc.).

`What does a reverse proxy do?`

- Protects your backend
- Handles heavy tasks
- loading balancing
- Routing

---

**Kafka** : Apache Kafka is a high-performance event streaming platform. It is used to send, receive, store, and process large amounts of data in real time between different systems. Think of it like a super-fast messaging system that connects different parts of an application.

Imagine you have many apps sending data every second: payments, notifications, logs, user clicks, order, analytics etc. Kafka collects all this data and streams it to other services without losing speed.

`Use of kafka : `

- Handles huge data
- Real-time data processing
- Decouples services - without kafka services talk directly with other services but with kafka, all communication goes through kafka (clean and scalable).
- Super reliable

---

| Kafka                                     | RabbitMQ                          |
| ----------------------------------------- | --------------------------------- |
| Best for **real-time streams & big data** | Best for **small message queues** |
| High throughput                           | Lower throughput                  |
| Stores data for long time                 | Usually deletes after reading     |

---

**Pub/Sub model** : The Publish–Subscribe model (Pub-Sub) is a way for different parts of a system to communicate without knowing each other directly.

It has two main roles:

1. Publisher – sends messages (events)

2. Subscriber – receives messages (events)

> They communicate through a broker like: Kafka, Redis Pub/Sub, RabbitMQ, Google Pub/Sub

`Why use Pub/Sub`

- Loose coupling : Systems don’t depend on each other directly.
- Real-time communication : Messages delivered immediately.
- Multiple subscribers : One message can go to 1 or 100 services at the same time.
- Scalable

---

| Pub-Sub                         | Queue                     |
| ------------------------------- | ------------------------- |
| Many consumers get same message | Only one consumer gets it |
| Good for broadcasting           | Good for background jobs  |
| Real-time                       | Ordered processing        |

---

**Ngrok** : Ngrok is a tool that creates a public URL for your local machine. It basically takes your local server (running on your laptop) and exposes it to the internet securely.

---

**Cron Jobs** : A cron job is a scheduled task that runs automatically at a specific time or interval on a server. examples : linux servers, backend applications, Devops, could services use cron jobs.

---

**Monolith** : The entire application is built, deployed, and run as a single unit.A monolithic app contains all components in one codebase and one deployment. All of are tightly coupled and run together.

Advantages of Monolith

- Easy to build (great for beginners & startups)
- Simple debugging
- Faster initial development
- Easy testing

Disadvantages of Monolith

- Hard to scale specific features
- Tight coupling (one bug can crash whole app)
- Slow deployments as app grows
- Hard for large teams
- Difficult to adopt new tech partially

---

**Micro-Services** : An application is broken into small, independent services where each service does one job and communicates with others via APIs.

Advantages of Microservices

✔ Independent deployment
✔ Easy to scale specific services
✔ Better fault isolation
✔ Multiple tech stacks allowed
✔ Suitable for large teams

Disadvantages of Microservices

❌ High complexity
❌ Network latency
❌ Difficult debugging
❌ Requires DevOps knowledge
❌ Costly infrastructure

--- 