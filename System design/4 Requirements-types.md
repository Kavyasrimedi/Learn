# System Design Requirements

Before designing any system, the first step is to identify its **requirements**.

Requirements define **what the system should do** and **how well it should perform**.

There are two types of requirements:

1. **Functional Requirements**
2. **Non-Functional Requirements**

---

# 1. Functional Requirements

## **Definition**

Functional requirements describe **what the system should do**.

They define the features, functionalities, and operations that users expect from the application.

Simply put,

> **Functional Requirements = Features of the application**

---

## Example: Amazon E-commerce Website

A user should be able to:

- Register an account
- Login
- Search for products
- Filter and sort products
- View product details
- Add products to cart
- Remove products from cart
- Apply coupon codes
- Place an order
- Make payments
- Track orders
- Cancel orders
- View order history
- Leave ratings and reviews
- Manage profile and addresses

These are all **functional requirements** because they describe **what the application allows users to do**.

---

## Characteristics of Functional Requirements

They describe:

- Features
- User interactions
- Business logic
- Workflows
- System behavior

Examples:

```text
✓ User can login
✓ User can search products
✓ User can make payments
✓ User can reset password
✓ User can upload profile picture
```

---

# 2. Non-Functional Requirements (NFRs)

## **Definition**

Non-functional requirements describe **how the system performs** rather than what it does.

They define the quality attributes of the application.

Simply put,

> **Non-Functional Requirements = Quality of the system**

---

# Example: Amazon E-commerce Website

The system should:

- Handle **1 million daily active users**
- Respond within **200 ms**
- Be available **99.9%** of the time
- Scale during festive sales (e.g., 10× traffic)
- Secure user data
- Continue working even if some servers fail

These requirements define the system's performance and reliability.

---

# Common Non-Functional Requirements

## 1. Scalability

The system should handle increasing traffic without significant performance degradation.

Example:

```text
Today:     100,000 users
Tomorrow: 1,000,000 users
```

The application should continue working efficiently.

---

## 2. Performance

Response time should remain low.

Example:

```text
Search Product

Desired Response Time:
< 200 ms
```

Lower response times improve user experience.

---

## 3. Availability

Availability measures how often the system remains operational.

Example:

```
99.9% Availability
```

This means the system is expected to be accessible almost all the time.

Higher availability:

- 99%
- 99.9%
- 99.99%
- 99.999% ("Five Nines")

---

## SLA vs SLO

### SLA (Service Level Agreement)

A formal commitment made to customers regarding service quality.

Example:

> "Our application will maintain **99.9% uptime**."

Breaking an SLA may result in penalties or compensation.

---

### SLO (Service Level Objective)

An internal engineering target that helps meet the SLA.

Example:

- Response time < 200 ms
- 99.95% server uptime
- Error rate < 0.1%

SLOs guide engineering teams in maintaining service quality.

> **Relationship:**  
> **SLO → helps achieve → SLA**

---

## 4. Security

The application should protect user data and prevent unauthorized access.

Examples:

- Data encryption
- HTTPS
- Authentication
- Authorization
- Secure password storage (Hashing)
- Secure payment processing

---

## 5. Reliability

The application should continue working correctly even when failures occur.

Examples:

- Database replication
- Automatic failover
- Backup and recovery

---

## 6. Fault Tolerance

The system should continue operating even if one or more components fail.

Example:

```text
Server 1 ❌

Server 2 ✅

Application still works.
```

This is achieved through:

- Load Balancers
- Replication
- Redundant servers
- Automatic failover

---

## 7. Scalability for Future Growth

The system should be designed to handle future increases in traffic.

Example:

```
Current Traffic : 100K users

Future Traffic : 1 Million users
```

The notes mention:

> "Scalable up to **10× traffic**"

This is a common non-functional requirement.

---

# Functional vs Non-Functional Requirements

| Functional Requirements | Non-Functional Requirements |
|--------------------------|-----------------------------|
| Defines **what** the system does | Defines **how well** the system performs |
| Features | Performance |
| User actions | Scalability |
| Business logic | Availability |
| Workflows | Reliability |
| APIs | Security |
| CRUD operations | Fault Tolerance |

---

# Example

## Functional Requirement

```text
User logs into Amazon.
```

## Non-Functional Requirement

```text
Login should complete within 200 ms.
```

---

## Functional Requirement

```text
User searches for products.
```

## Non-Functional Requirement

```text
Search results should appear within 150 ms,
even with 1 million concurrent users.
```

---

# How Requirements Drive System Design

Requirements determine the architecture of the system.

Example:

```
Functional Requirement:
User uploads videos.
```

This tells us **what** the application should support.

Now consider the NFRs:

```
- 10 million users
- <300 ms response time
- 99.99% availability
- Global access
```

These requirements influence architectural decisions such as:

- CDN for video delivery
- Load Balancers
- Distributed Storage
- Caching
- Database Replication
- Auto Scaling

---

# Key Takeaway

Before designing any system, always identify **both** types of requirements.

```text
Requirements
     │
     ├──────────────┐
     │              │
     ▼              ▼
Functional      Non-Functional
     │              │
What?         How Well?
     │              │
Features      Performance
               Scalability
               Availability
               Security
               Reliability
               Fault Tolerance
```

A good system design satisfies **both**:

- Functional requirements ensure the system **works correctly**.
- Non-functional requirements ensure the system **works efficiently, reliably, and at scale**.
