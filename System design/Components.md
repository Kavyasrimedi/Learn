# Components of System Design

A modern software system is typically composed of several key components that work together to handle requests, process data, and serve users efficiently.

---

# 1. Data

Data is the core of every system.

Examples:

- Images
- Videos
- Audio
- Text
- User information
- Transaction records

### **Database**

A database is used to store data so that it can be efficiently retrieved, updated, and managed.

### **Types of Databases**

#### SQL Databases

- Structured data
- Tables, rows, and columns
- Strong consistency
- Examples:
  - MySQL
  - PostgreSQL
  - SQL Server

#### NoSQL Databases

- Flexible schema
- Suitable for large-scale applications
- Better horizontal scalability

Examples:

- MongoDB
- Cassandra
- DynamoDB

---

# 2. Application Code

Application code contains the business logic of the system.

It acts as a layer between the client and the database.

### **Responsibilities**

- Process user requests
- Validate input
- Apply business rules
- Interact with databases
- Return responses to clients

### **APIs**

Application code exposes APIs that hide the complexity of:

- Database tables
- SQL queries
- Internal implementation details

### **Common Operations (CRUD)**

- Create (Insert)
- Read (Retrieve)
- Update
- Delete

### **Endpoints**

Endpoints provide access to application functionality.

Examples:

```http
GET /users
POST /users
PUT /users/1
DELETE /users/1
```

---

# 3. Client Application

The client application is the interface through which users interact with the system.

Examples:

- Web applications
- Mobile applications
- Desktop applications

### **Request Flow**

```text
Client
   │
   ▼
Application Code
   │
   ▼
Database
```

The client sends requests to the application, which processes them and interacts with the database.

---

# 4. Server

Application code must run somewhere.

That place is called a **Server**.

### **Responsibilities**

- Host application code
- Process incoming requests
- Communicate with databases
- Return responses to clients

### **Examples**

- Physical Servers
- Virtual Machines
- Cloud Servers

Examples of cloud providers:

- AWS
- Azure
- Google Cloud

### **Inter-Service Communication**

Servers can also communicate with other servers using APIs.

```text
Server A  ←→  Server B
```

This forms the basis of distributed systems and microservices.

---

# 5. Cache

A cache stores frequently accessed data temporarily so that it can be retrieved much faster than querying the database repeatedly.

### **Purpose**

- Reduce database load
- Improve response time
- Improve user experience

### **Example**

Without Cache:

```text
User Request
      ↓
   Database
      ↓
   Response
```

With Cache:

```text
User Request
      ↓
    Cache
      ↓
 (If Found)
      ↓
   Response
```

Only if data is not found in the cache does the application query the database.

### **Popular Cache Technologies**

- Redis
- Memcached

---

# 6. Load Balancer

When multiple servers are available, a load balancer distributes incoming requests among them.

### **Responsibilities**

- Distribute traffic evenly
- Prevent server overload
- Improve availability
- Improve scalability
- Perform health checks

### **Health Checks**

The load balancer continuously checks whether servers are healthy.

If a server fails:

```text
Server 1 ❌
Server 2 ✅
Server 3 ✅
```

Traffic is automatically redirected to healthy servers.

### **Architecture**

```text
Client
   │
   ▼
Load Balancer
   │
 ┌─┴─┐
 ▼   ▼
S1   S2
```

### **Benefits**

- Better resource utilization
- Fault tolerance
- High availability

---

# 7. Message Queue

Message queues are used for asynchronous processing.

Instead of processing everything immediately, requests can be placed into a queue and handled later.

### **Why Use It?**

Some tasks take time:

- Sending emails
- Sending SMS messages
- Generating reports
- Processing videos

Users should not wait for these operations to complete.

### **Architecture**

```text
Application
      │
      ▼
Message Queue
      │
      ▼
 Worker Service
      │
      ▼
 SMS / Email Service
```

### **Benefits**

- Faster user response times
- Better scalability
- Improved reliability

### **Popular Message Queues**

- RabbitMQ
- Apache Kafka
- Amazon SQS

---

# 8. Monitoring & Logs

Monitoring helps track the health and performance of the system.

Logging records events and activities happening inside the system.

### **Monitoring Tracks**

- CPU usage
- Memory usage
- Server health
- Response times
- Error rates

### **Logs Track**

- User requests
- System errors
- Database operations
- Application events

### **Benefits**

- Easier debugging
- Performance analysis
- Early issue detection
- Reliability improvements

### **Popular Tools**

- Prometheus
- Grafana
- ELK Stack
- Datadog

---

# Overall Architecture

```text
                Client
                   │
                   ▼
            Load Balancer
                   │
        ┌──────────┴──────────┐
        ▼                     ▼
     Server 1             Server 2
(Application)        (Application)
        │                     │
        └──────────┬──────────┘
                   ▼
                Cache
                   │
                   ▼
               Database
                   │
                   ▼
            Message Queue
                   │
                   ▼
            Worker Services

         Monitoring & Logs
                ▲
                │
      Tracks all components
```

---

# Key Takeaway

A typical system design consists of:

1. **Data** → What needs to be stored.
2. **Database** → Where data is stored.
3. **Application Code** → Business logic.
4. **Server** → Runs the application.
5. **Cache** → Speeds up data retrieval.
6. **Load Balancer** → Distributes traffic.
7. **Message Queue** → Handles asynchronous tasks.
8. **Monitoring & Logs** → Tracks system health and activity.

Together, these components help build systems that are:

- Scalable
- Reliable
- Maintainable
- High Performing
- Fault Tolerant
