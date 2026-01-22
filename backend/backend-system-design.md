#### Architectural Style

**Monolith**

- Single deployable unit
- Simple to develop, test, and deploy initially
- Suitable for early-stage products or small teams
  > Becomes hard to scale teams and deployments independently

**Modular monolith** (Recommended starting point)

- Single deployment, but code is strictly modularized
- Clear boundaries between domains (DDD-inspired)
- Easier migration to microservices later

**Microservices**

- Independently deployable services
- Scales teams and workloads independently
- Required for large systems with distinct domains

> Higher operational complexity (network calls, observability, DevOps)

#### Scalability Strategy

**Vertical Scaling**

- Adding more resources (CPU, RAM) to a single server
- Simpler to manage, but has limits (single point of failure, hardware max)

**Horizontal Scaling**

- Adding more servers (nodes) to distribute the load
- Achieves high availability and fault tolerance
- More complex to implement (load balancing, distributed data)

#### API Design & Communication

**Synchronous (HTTP / REST / gRPC)**

- Simple request-response model
- Suitable for user-facing services
- Easier to debug
- Example :
  - REST: Widely adopted, human-readable, flexible (JSON/XML)
  - gRPC: High performance, efficient (Protobuf), strong typing, better for microservices communication

**Asynchronous (Message Queues / Event Streams)**

- Decouples services, improves responsiveness, handles spikes
- Examples: Kafka, RabbitMQ, SQS
- Suitable for background tasks, event-driven architectures, long-running processes

#### Data Architecture
**Relational (PostgreSQL, MySQL)**
- Structured data with relationships
- ACID compliance with consistency 
- Complex queries and transactions

**NoSQL (MongoDB, DynamoDB, Cassandra)**
- High throughput and horizontal scalability
- Eventual consistency

#### Caching Strategy (Reduces database load, Improves latency dramatically)
**Caching Layers**
- client side cache (browser cache, mobile app cache)
- server side cache (in-memory caches like Redis, Memcached)
- CDN (Content Delivery Networks) for static assets
- Database cache (query results, frequently accessed data)

**Cache Patterns**
- Cache-aside: Application checks cache first, then DB if miss
- Read-through: Cache automatically loads data from DB on miss
- Write-through: Cache writes data to DB and cache simultaneously
- Write-back: Cache writes data to cache first, then asynchronously to DB

#### Load Balancing & Traffic Management
**Load Balancing Techniques**
- Round Robin: Distributes requests evenly across servers
- Least Connections: Directs traffic to the server with the fewest active connections
- Least Response Time: Directs traffic to the server with the fastest response time
- IP Hash: Directs requests from the same IP to the same server
- Weighted Round Robin: Distributes requests based on server capacity

**Load Balancers**
- Hardware Load Balancers (F5, Citrix ADC)
- Software Load Balancers (Nginx, HAProxy)
- Cloud Load Balancers (AWS ELB, Azure Load Balancer, GCP Load Balancer)

***types*** - L4/L7 Load Balancers:
  - L4 (Transport Layer): Operates at the TCP/UDP level, faster, simpler, based on IP/port.
  - L7 (Application Layer): Operates at the HTTP/HTTPS level, more intelligent, can inspect content, SSL termination, URL routing.
  

**Traffic Management**
- DNS Load Balancing: Distributes traffic at the DNS level
- CDN: Caches content geographically closer to users
- API Gateway: Centralized entry point for microservices, handles routing, authentication, rate limiting

#### Security Best Practices
**Authentication**
- JWT (JSON Web Tokens): Stateless, scalable, good for APIs.
- OAuth 2.0: Authorization framework for third-party access.
- Multi-Factor Authentication (MFA): Adds an extra layer of security.

**Authorization**
- RBAC (Role-Based Access Control): Assigns permissions based on user roles.
- ABAC (Attribute-Based Access Control): Dynamic authorization based on attributes.

**Data Protection**
- Encryption: Encrypt data at rest and in transit (TLS/SSL).
- Hashing: Store passwords as hashes (bcrypt, Argon2).
- Input Validation: Prevent injection attacks (SQL, XSS).

**Network Security**
- Firewalls: Control network traffic.
- DDoS Protection: Mitigate denial-of-service attacks.
- Rate Limiting: Prevent abuse and brute-force attacks.

#### Monitoring & Observability
**Logging**
- Centralized Logging: Aggregate logs from all services (ELK Stack, Splunk, Datadog).
- Structured Logging: Log in JSON format for easier parsing and analysis.

**Metrics**
- Prometheus/Grafana: Collect and visualize time-series metrics.
- Application Performance Monitoring (APM): Track application performance (New Relic, Dynatrace).

**Tracing**
- Distributed Tracing: Follow requests across multiple services (Jaeger, Zipkin).
- Correlate Logs, Metrics, Traces: Gain a holistic view of system health.

#### Disaster Recovery & Backup
**Backup Strategy**
- Regular Backups: Schedule automated backups for databases and critical data.
- Offsite Storage: Store backups in a separate geographical location.
- Point-in-Time Recovery: Ability to restore data to a specific timestamp.

**Disaster Recovery Plan**
- RTO (Recovery Time Objective): Maximum acceptable downtime.
- RPO (Recovery Point Objective): Maximum acceptable data loss.
- Redundancy: Deploy services across multiple availability zones or regions.
- Failover: Automatic switching to a standby system in case of failure.

#### DevOps & CI/CD
**Continuous Integration (CI)**
- Automated Builds: Automatically build and test code changes.
- Version Control: Use Git for source code management.
- Code Reviews: Ensure code quality and catch issues early.

**Continuous Delivery/Deployment (CD)**
- Automated Deployments: Deploy








