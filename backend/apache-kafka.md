**Kafka** : Apache Kafka is a high-performance event streaming platform. It is used to send, receive, store, and process large amounts of data in real time between different systems. Think of it like a super-fast messaging system that connects different parts of an application.

Imagine you have many apps sending data every second: payments, notifications, logs, user clicks, order, analytics etc. Kafka collects all this data and streams it to other services without losing speed.

`Use of kafka : `

- Handles huge data
- Real-time data processing
- Decouples services - without kafka services talk directly with other services but with kafka, all communication goes through kafka (clean and scalable).
- Super reliable

`Where kafka is used :`
| Company Use Case | Example |
| ---------------- | -------------------------------------------------- |
| Netflix | Streams viewing events, analytics, recommendations |
| Uber | Tracks rides, drivers, locations in real time |
| Amazon | Order tracking, inventory update across systems |
| Banks | Fraud detection, real-time transactions |

`Core Concepts of Kafka`
| Term | Meaning |
| ------------------ | -------------------------------------------------------------- |
| **Producer** | Application that sends messages to Kafka |
| **Consumer** | Application that reads messages from Kafka |
| **Broker** | Kafka server storing messages |
| **Topic** | A category or channel where messages are sent (e.g., "orders") |
| **Partition** | Splitting a topic into multiple pieces for scalability |
| **Consumer Group** | Multiple consumers sharing workload of one topic |

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

**What is kafka topic?**

> A topic is a logical channel where producers send messages and consumers read them.

**What is a partition in Kafka?**

> A partition is a sub-division of a topic that enables parallel processing and scalability.
> **What is a Kafka broker?**
> A broker is a Kafka server that stores data and serves producer and consumer requests.

**What is a Kafka cluster?**

> A cluster is a group of brokers working together to provide scalability and fault tolerance.

**What is offset in Kafka?**

> An offset is a unique ID assigned to each message in a partition, used by consumers to track their position.

**What is a consumer group?**

> A consumer group is a set of consumers that share the load of reading data from a topic. Each partition is read by only one consumer per group.

**What is Kafka used for in microservices?**

> Kafka is used for event-driven communication, service decoupling, and asynchronous processing.

**What is Kafka Streams?**
> Kafka Streams is a library for real-time stream processing directly on Kafka data.