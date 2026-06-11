## RESOURCES
youtube - bytebytego (https://www.youtube.com/results?search_query=bytebytego+system+design) <br>
repo - (https://github.com/Kavyasrimedi/awesome-system-design-resources) <br>
website - (https://codejeet.com/system-design/scale-from-zero-to-millions-of-users) <br>

## Day 1 - Telusuko (https://www.youtube.com/watch?v=Vnm-ycSfJx4)
# System Design

## **Definition**

- Making a system or application work seamlessly, even when millions of users are using it simultaneously.
- Building large-scale applications that are scalable, maintainable, and reliable.

### **Breaking Down the Term**

**System**  
A collection of components working together to achieve one or more use cases.

**Design**  
Planning and organizing the internal structure of a system to solve existing and potential problems efficiently.

# What Does System Design Involve?

System design is the process of:

1. Identifying issues and bottlenecks.
2. Understanding their impact on users and the system.
3. Designing solutions.
4. Optimizing those solutions.
5. Handling new challenges introduced by those optimizations.

# Key Takeaway

System design is not just about solving a problem.

It is an iterative process:

**Problem → Solution → Optimization → New Problem → Better Solution**
# Example: Bank System

Consider:

- **System:** AB Bank
- **Design:** Managing customer operations and banking processes efficiently.

### **Customer Flow**

1. Customer arrives at the counter.
2. Customer deposits or withdraws money.
3. Receipt is generated.
4. Customer leaves.

---

# What Does System Design Involve?

System design is the process of:

1. Identifying issues and bottlenecks.
2. Understanding their impact on users and the system.
3. Designing solutions.
4. Optimizing those solutions.
5. Handling new challenges introduced by those optimizations.

---

# Issue 1: Slow Processing

### **Current Situation**

Assume a cashier takes **10 minutes** to serve one customer.

- Customers served per hour = **6**

### **Cashier Tasks**

1. Understand customer requirements.
2. Count cash manually.
3. Prepare and generate the receipt.

### **Solution**

- Train the cashier to count cash faster.
- Improve typing speed and familiarity with the system.

### **Result**

- Processing time reduced by **50%**.
- New processing time = **5 minutes per customer**.

### **Software Analogy**

In software systems, this is similar to:

- Improving algorithms.
- Optimizing database queries.
- Writing cleaner code.

**Goal:** Improve code quality and execution speed.

Examples:

- Low-Level Design (LLD)
- Data Structures & Algorithms (DSA)
- Code Optimization

---

# Issue 2: Increasing Customer Volume

### **Problem**

As customer traffic grows, a single cashier becomes a bottleneck.

### **Solution**

- Increase workstation efficiency.
- Introduce cash-counting machines.

### **Result**

- Manual cash counting is eliminated.
- Processing time reduced to **3 minutes per customer**.

### **System Design Concept**

This is an example of **Vertical Scaling**.

Instead of adding more counters, we improve the capability of the existing counter by providing better resources.

Examples in software:

- Increasing CPU power.
- Increasing RAM.
- Upgrading storage.
- Using faster hardware.

---

# Issue 3: Long Waiting Times

### **Problem**

Even after optimization, customers still wait in a queue.

Example:

- The 10th customer may need to wait **27 minutes** before being served.

### **Solution**

- Add two additional cash counters.

### **Result**

- Waiting time decreases significantly.

### **System Design Concept**

This is an example of **Horizontal Scaling**.

Instead of making one counter stronger, we add multiple counters to handle more customers simultaneously.

Examples in software:

- Multiple application servers.
- Multiple backend instances.
- Distributed services.

---

# Issue 3.1: Data Consistency Problem

Adding multiple counters introduces a new challenge.

### **Scenario**

Suppose:

- Counter 1 maintains Database A.
- Counter 2 maintains Database B.

### **Problem**

- Customer information becomes fragmented.
- One counter may not know about data stored by another counter.
- Customer information becomes inconsistent across counters.
- Operations may fail due to missing or outdated information.

### **Solution**

Use a **Centralized Database**.

All counters access the same customer data source.

### **Architecture**

```text
Counter 1 ─┐
           │
Counter 2 ─┼──► Centralized Database
           │
Counter 3 ─┘
```

### **Result**

- Data remains consistent.
- Every counter can access the latest customer information.
- Duplicate or conflicting records are avoided.

---

# Issue 4: Uneven Traffic Distribution

### **Problem**

Even after introducing multiple counters and a centralized database, customers tend to choose the nearest counter.

This creates:

- Long queues at some counters.
- Idle or underutilized counters elsewhere.
- Uneven workload distribution.

### **Example**

```text
Counter 1 → 20 Customers Waiting
Counter 2 → 2 Customers Waiting
Counter 3 → 1 Customer Waiting
```

Although sufficient resources exist, they are not being utilized efficiently.

### **Solution**

Introduce a **Middleman** that directs customers to counters based on queue length and availability.

### **System Design Concept**

This middleman acts as a **Load Balancer**.

### **Architecture**

```text
Customers (Requests)
        │
        ▼
  Load Balancer
   /    |    \
  ▼     ▼     ▼
Server1 Server2 Server3
   \      |      /
        ▼
  Centralized DB
```

### **Role of Load Balancer**

- Distributes incoming traffic evenly.
- Prevents overload on a single server.
- Improves resource utilization.
- Reduces response time.
- Improves availability and scalability.

### **Result**

- Balanced workload across all counters.
- Reduced waiting time.
- Better utilization of available resources.
- Improved user experience.

---

# Evolution of the Bank System

### **Stage 1**

```text
Customers
    │
    ▼
Single Counter
```

Problem:
- Slow processing
- Long waiting times

---

### **Stage 2**

```text
Customers
    │
    ▼
Improved Counter
(Cash Counting Machine)
```

Problem:
- Still limited by a single counter

---

### **Stage 3**

```text
Customers
      │
 ┌────┴────┐
 ▼         ▼
Counter1 Counter2
```

Problem:
- Data inconsistency

---

### **Stage 4**

```text
Customers
      │
 ┌────┴────┐
 ▼         ▼
Counter1 Counter2
      │
      ▼
Centralized Database
```

Problem:
- Uneven traffic distribution

---

### **Stage 5**

```text
Customers
      │
      ▼
Load Balancer
   /   |   \
  ▼    ▼    ▼
 C1   C2   C3
   \   |   /
      ▼
Centralized Database
```

Result:
- Scalability
- Consistency
- Better performance
- Reduced waiting time

---

# Key Takeaway

System design is not about creating a perfect system on the first attempt.

It is a continuous cycle:

```text
Problem
   ↓
Solution
   ↓
Optimization
   ↓
New Problem
   ↓
Better Solution
   ↓
Scale Further
```

The goal is to continuously improve the system while maintaining:

- Scalability
- Reliability
- Performance
- Availability
- Maintainability
- Consistency
- User Experience

This problem-solving and optimization mindset forms the foundation of modern software system design.
