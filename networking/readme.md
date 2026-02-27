**What is a Computer Network?**
A computer network is a group of connected devices that communicate and share resources using protocols. example : LAN, Internet.

---

**What is a Protocol?**
A protocol is a set of rules that define how data is transmitted and received between devices over a network.

**_Without protocols, devices cannot understand, how to send data, how to receive data, how to interpret data._**

**Need of protocol**

- Data format – structure of message
- Transmission method – how data is sent
- Error handling – what to do if data is lost
- Addressing – where data should go
- Security – encryption and authentication

---

1. **IP (Internet Protocol) :** Identifies devices and delivers packets to correct destination, Every device has an IP address, its works like an home address. IP is responsible for addressing and routing packets between devices.

2. **TCP (Transmission Control Protocol) :**Reliable data transmission, Connection-oriented, Error checking, Ensures data arrives in order, Retransmits lost data. TCP ensures reliable and ordered delivery of data.

3. **UDP (User Datagram Protocol) :** Fast but unreliable transmission, No error checking, No guarantee of delivery, Faster than TCP. Used in video streaming, gaming, live calls. UDP provides fast communication without reliability guarantee.

4. **HTTP (HyperText Transfer Protocol) :** used in browser, websites. HTTP is used for communication between web browser and web server.

5. **HTTPS (Secure HTTP) :** Secure web communication using SSL/TLS encryption.

6. **SMTP (Simple Mail Transfer Protocol) :** Send emails

7. **POP3 (post office protocol 3) / IMAP (internet message access protocol) :** used to receive mails.

- POP3 → Download and delete from server
- IMAP → Sync with server

---

**How protocols work together**
Example: Opening google.com

- Step 1: DNS → get IP address
- Step 2: TCP → establish connection
- Step 3: HTTPS → secure communication
- Step 4: IP → route packets

---

**What is difference between TCP and UDP?**
TCP is reliable and connection-oriented, while UDP is fast and connectionless. TCP ensures: delivery, order, error correction but UDP does not guarantee delivery but is faster.

---

**Why TCP is slower than UDP?**
TCP performs: error checking, acknowledgment, retransmission, UDP does not perform these, so it is faster.

---

**What is DNS and why needed?**
DNS converts domain names into IP addresses because computers communicate using IP addresses, not domain names.

---

**What happens when you enter google.com in browser?**

- Browser sends DNS request
- DNS returns IP address
- TCP connection established
- HTTPS request sent
- Server responds with webpage

**What is IP address?**
IP address is a unique identifier assigned to each device on network for communication.

---

**Difference between pop3 and imap.**

POP3 downloads emails from the mail server to the local device and usually deletes them from the server.

**_How it works_**

- Email is downloaded to your computer 📥
- Email is removed from the server (by default)
- Email stored locally only

**\*Characteristics :** Works offline after download, No synchronization between multiple devices, Emails stored on single device

**IMAP (Internet Message Access Protocol)**
IMAP synchronizes emails between server and multiple devices without deleting them from the server.

**_How it works:_**

- Email stays on server ☁️
- All devices sync with server
- Changes reflect everywhere

**Characteristics:** Supports multiple devices, Real-time synchronization, emails stored on server.

---

**What is MAC address?**
MAC address is a unique physical address assigned to network interface card (NIC). Used in local network communication.

---

**Difference between IP and MAC address**
| IP address | MAC address |
| ------------------- | ------------------------ |
| Logical address | Physical address |
| Assigned by network | Assigned by manufacturer |
| Can change | Cannot change |
| Used in internet | Used in LAN |

---

**What is DHCP?**
Dynamic Host Configuration Protocol (DHCP) is a network management protocol that automatically assigns IP addresses, subnet masks, default gateways, and other configuration details to devices on a network. DHCP automatically assigns IP addresses to devices in network. Without DHCP, we must assign IP manually.

---

**What is Router?**
Router connects different networks and forwards data packets. example : Connects your home network to internet.

---

**What is Switch?**
Switch connects devices within same network and uses MAC address to send data.

---

**Difference between Router and Switch?**
| Router | Switch |
| --------------------------- | -------------------------------- |
| Connects different networks | Connects devices in same network |
| Uses IP address | Uses MAC address |

---

> Socket = IP address + Port number

---

**What is Firewall?**
Firewall is a security system that controls incoming and outgoing network traffic.

**What is Packet?**
Packet is a small unit of data transmitted over network.

**What is Bandwidth?**
Bandwidth is maximum data transfer capacity of network.

**What is Latency?**
Latency is delay in data transmission. Measured in milliseconds.

---

**What is a Port?**
A port is a logical endpoint used by protocols to identify specific services on a device. example : 192.168.1.10:80 --> 192.168.1.10 → device, 80 → web service

| Protocol            | Port   | Purpose                     |
| ------------------- | ------ | --------------------------- |
| HTTP                | 80     | Web communication           |
| HTTPS               | 443    | Secure web communication 🔒 |
| FTP                 | 21     | File transfer               |
| SSH                 | 22     | Secure remote login         |
| Telnet              | 23     | Remote login (not secure)   |
| SMTP                | 25     | Send email                  |
| DNS                 | 53     | Domain name resolution      |
| DHCP                | 67, 68 | Assign IP address           |
| POP3                | 110    | Receive email               |
| IMAP                | 143    | Receive email (sync)        |
| SNMP                | 161    | Network monitoring          |
| HTTPS (secure SMTP) | 465    | Secure email sending        |
| IMAP Secure         | 993    | Secure IMAP                 |
| POP3 Secure         | 995    | Secure POP3                 |
| MySQL               | 3306   | Database                    |
| PostgreSQL          | 5432   | Database                    |
| RDP                 | 3389   | Remote desktop              |

---

**OSI Model**
The OSI model is a 7-layer framework that defines how data is transmitted between devices in a network.

Each layer has specific responsibility. These are 7 layers from top to bottom.

- Application
- Presentation
- Session
- Transport
- Network
- Data Link
- Physical

**_Trick : All People Seem To Need Data Processing_**

**\*Application Layer :\*\*** Provides interface to user applications,Application layer provides services to user applications. example : https, ftp, smtp, dns.

**_Presentation Layer_** : Data formatting, encryption, compression example : SSL/TLS encryption, Data encoding. Presentation layer handles encryption and formatting.

**_Session Layer_** : Manages connection sessions, Session layer establishes and manages communication sessions.

**_Transport Layer_** : TCP, UDP, Reliable delivery, Flow control, Transport layer ensures reliable end-to-end communication.

**_Network Layer_** : Network layer handles routing using IP addresses.

**_Data Link Layer_** : Data link layer uses MAC address for communication.

**_Physical Layer_** :Physical transmission of bits example : cable, electric signal. Physical layer transmits raw bits over medium.

---

**Real example while opening a website using OSI layers**
Application → HTTP request
Presentation → encrypt (HTTPS)
Session → establish session
Transport → TCP sends data
Network → IP routes data
Data Link → MAC address used
Physical → bits transmitted via cable

---

**Which devices work on which layers?**
| Device | Layer |
| ------ | --------------- |
| Router | Network layer |
| Switch | Data link layer |
| Hub | Physical layer |

---

**Which layer is closest to user?**
Application layer.

---

**Explain data flow from sender to receiver using OSI model**
Data flows from Application layer → Presentation → Session → Transport → Network → Data Link → Physical layer on sender side, and reverse on receiver side.

---

**TCP/IP model**
The TCP/IP model is a 4-layer networking model that defines how data is transmitted over the internet.

4. Application Layer
5. Transport Layer
6. Internet Layer
7. Network Access Layer

