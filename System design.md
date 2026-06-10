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

---

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
3. Generate the receipt.

### **Solution**

- Train the cashier to count cash faster.
- Improve typing speed and system familiarity.

### **Result**

- Processing time reduced by **50%**.
- New processing time = **5 minutes per customer**.

---

# Issue 2: Increasing Customer Volume

As customer traffic grows, the cashier becomes a bottleneck.

### **Solution**

- Introduce cash-counting machines.
- Improve workstation efficiency.

### **Result**

- Manual cash counting is eliminated.
- Processing time reduced to **3 minutes per customer**.

---

# Issue 3: Long Waiting Times

### **Problem**

Even with faster processing, customers still wait in a queue.

Example:

- The 10th customer may need to wait **27 minutes** before being served.

### **Solution**

- Add two additional cash counters.

### **Result**
- Waiting time decreases significantly.

---

# Issue 3.1: Data Consistency Problem

Adding multiple counters introduces a new challenge.

### **Scenario**

Suppose:

- Counter 1 maintains Database A.
- Counter 2 maintains Database B.

### **Problem**

- Customer information becomes fragmented.
- One counter may not have access to data stored by another counter.
- This leads to inconsistency and operational conflicts.

### **Possible Solution**

Use a **shared centralized database** or a **synchronized distributed database** so that all counters access the same customer information.

---

# Key Takeaway

System design is not just about solving a problem.

It is an iterative process:

**Problem → Solution → Optimization → New Problem → Better Solution**

The goal is to continuously improve the system while maintaining:

- Scalability
- Reliability
- Performance
- Maintainability
- Consistency
- User Experience

This mindset forms the foundation of modern software system design.
