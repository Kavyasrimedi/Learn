# Types of Applications in System Design

The type of application largely determines how the system should be designed.

Different applications face different bottlenecks, and therefore require different optimization strategies.

---

# Understanding the Problem

Consider two applications:

- Same number of users
- Same network conditions
- Both experience latency

### **What is Latency?**

Latency is the time taken by a system to respond to a request.

```text
User Request
      │
      ▼
   Processing
      │
      ▼
   Response

Latency = Total Time Taken
```

---

# How Can Latency Be Reduced?

Depending on the bottleneck, latency can be reduced by:

- Adding more databases
- Using better caching strategies
- Database replication
- Database sharding
- Upgrading CPU/GPU resources
- Improving network infrastructure
- Optimizing application code

The correct solution depends on the type of application.

---

# Two Major Categories of Applications

Applications can broadly be divided into:

1. **Data-Intensive Applications**
2. **Compute-Intensive Applications**

Understanding which category your system belongs to is one of the first steps in system design.

---

# 1. Data-Intensive Applications

## **Definition**

Data-intensive applications spend most of their time:

- Storing data
- Retrieving data
- Moving data
- Synchronizing data

The challenge is usually not computation.

The challenge is handling large volumes of data efficiently.

---

## **Common Bottlenecks**

- Slow database queries
- Network latency
- Database overload
- Data consistency issues
- Storage limitations
- High read/write traffic

### **Typical Causes**

```text
User Request
      │
      ▼
Application
      │
      ▼
Database
      │
      ▼
Response
```

Most of the time is spent waiting for data.

---

## **Examples**

### Social Media

- Instagram Feed
- Facebook Timeline
- Twitter/X Feed

### Messaging

- WhatsApp Messages
- Telegram Chats

### Banking

- Bank Transactions
- Payment Systems

### Analytics

- Log Processing Systems
- Event Tracking Systems

---

## **Questions to Worry About**

### Data Access

- How quickly can data be read?
- How quickly can data be written?

### Reliability

- How safely is data stored?
- What happens if a database fails?

### Scale

- How many users can access the system simultaneously?
- Can the database handle peak traffic?

### Consistency

- Will all users see the same data?
- How do we prevent stale data?

---

## **Typical Solutions**

### Caching

Store frequently accessed data closer to users.

Examples:

- Redis
- Memcached

---

### Database Replication

Create multiple copies of the database.

Benefits:

- Faster reads
- Higher availability

---

### Database Sharding

Split large databases into smaller partitions.

Benefits:

- Better scalability
- Reduced load per database

---

### Content Delivery Networks (CDNs)

Store content closer to users geographically.

Useful for:

- Images
- Videos
- Static files

---

# Example: Instagram Feed

Instagram Feed is primarily a **data-intensive application**.

### Why?

The application continuously:

- Reads posts
- Fetches comments
- Loads stories
- Retrieves user profiles
- Delivers images and videos

Most time is spent fetching and delivering data.

---

## Challenges

- Millions of users reading data simultaneously
- Huge storage requirements
- Data consistency
- Fast image and video delivery

---

## How Instagram Scales

- Multiple databases
- Database replication
- Aggressive caching
- CDN for media delivery
- Distributed storage systems

---

# 2. Compute-Intensive Applications

## **Definition**

Compute-intensive applications spend most of their time performing calculations.

The amount of data may be relatively small, but the processing is complex.

### Characteristics

- Heavy mathematical computations
- CPU-intensive workloads
- GPU-intensive workloads
- Parallel processing requirements

---

## **Common Bottlenecks**

- CPU limitations
- GPU limitations
- Algorithm complexity
- Long processing times

---

## **Examples**

### Artificial Intelligence

- Machine Learning Training
- Deep Learning Models
- Large Language Models (LLMs)

### Media Processing

- Image Processing
- Video Rendering
- Video Encoding

### Scientific Computing

- Simulations
- Weather Forecasting
- Physics Engines

### Security

- Cryptography
- Encryption Systems

---

## **Questions to Worry About**

### Performance

- How fast can we compute results?
- Can we reduce execution time?

### Parallelization

- Can the workload run on multiple machines?
- Can tasks be processed concurrently?

### Hardware Utilization

- Should we use GPUs instead of CPUs?
- Can specialized hardware improve performance?

### Cost

- How can computational cost be reduced?
- Can algorithms be optimized?

---

## **Typical Solutions**

### Better Algorithms

Example:

```text
O(n²)  →  O(n log n)
```

Improving the algorithm often provides the biggest performance gains.

---

### Parallel Processing

Split work across multiple machines.

```text
Task
 │
 ├── Machine 1
 ├── Machine 2
 └── Machine 3
```

---

### GPU Acceleration

GPUs can process thousands of operations simultaneously.

Useful for:

- AI Training
- Matrix Computations
- Simulations

---

### Distributed Computing

Run computations across multiple servers.

Examples:

- Apache Spark
- Ray
- Distributed ML Training

---

# Example: Flight Simulator Training System

Suppose an aviation company wants to train more pilots.

### Challenge

A single simulator machine can train only a limited number of pilots.

### Possible Improvements

- Add more simulator machines
- Run simulations in parallel
- Use GPUs instead of CPUs
- Optimize simulation algorithms
- Reduce computation costs

### Focus

The main challenge is computation, not data storage.

Therefore, this is a **compute-intensive application**.

---

# Hybrid Systems

Many real-world systems are both data-intensive and compute-intensive.

---

## Example: YouTube

### Data-Intensive Part

Serving videos:

```text
User
  │
  ▼
Video Storage
  │
  ▼
Video Streaming
```

Challenges:

- Massive storage
- High bandwidth
- CDN distribution

---

### Compute-Intensive Part

Video recommendations:

```text
User Activity
       │
       ▼
Recommendation Model
       │
       ▼
Suggested Videos
```

Challenges:

- ML inference
- Ranking algorithms
- Personalization

---

# Quick Trick to Identify the Bottleneck

Ask:

### Where is the system spending most of its time?

#### If time is spent moving or retrieving data:

```text
Database
Network
Storage
Cache
```

➡️ **Data-Intensive Problem**

---

#### If time is spent performing calculations:

```text
CPU
GPU
Algorithms
Model Inference
```

➡️ **Compute-Intensive Problem**

---

# Key Takeaway

Before designing any system, identify the primary bottleneck.

```text
Data Bottleneck
      ↓
Data-Intensive Design
(Cache, DBs, Replication, CDNs)

Computation Bottleneck
      ↓
Compute-Intensive Design
(GPUs, Parallelism, Better Algorithms)
```

The best system design solution depends on whether the problem is primarily about **moving data** or **processing data**.
