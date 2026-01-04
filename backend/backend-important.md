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

**Data PipeLines** : In software engineering, a data pipeline is a set of automated processes that move data from one place to another, transforming it along the way.
