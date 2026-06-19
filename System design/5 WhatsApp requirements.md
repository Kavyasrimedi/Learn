# Example: WhatsApp Requirements

When designing a system like **WhatsApp**, we first identify its **Functional Requirements** (what the system should do) and **Non-Functional Requirements** (how well the system should perform).

---

# Functional Requirements

These describe the features that WhatsApp should provide to users.

## User Management

- Register/Login using phone number
- Add and save contacts
- Manage user profile (name, photo, about)

---

## Messaging

- Send text messages
- Receive text messages
- Send media (images, videos, documents, audio)
- Receive media
- Download media
- Forward messages
- Reply to messages
- Delete messages
- Delete messages for everyone *(within the allowed time window)*

---

## Voice & Video Communication

- Make voice calls
- Receive voice calls
- Accept or reject calls
- Make video calls
- Group voice/video calls

---

## Status

- Upload status
- View status
- React to status
- Share status

---

## Contact Management

- Block contacts
- Unblock contacts
- Delete chats
- Archive chats
- Mute conversations

---

## Payments *(Optional Feature)*

- Send money
- Receive money
- Link bank account / UPI
- View transaction history

---

## External Integration

- Open website links
- Open map locations
- Share live location
- Share contacts

---

# Non-Functional Requirements

These describe **how well** WhatsApp should perform.

---

## Scalability

The system should:

- Handle millions (or billions) of users.
- Support millions of concurrent connections.
- Scale automatically during peak traffic.

---

## Performance

- Messages should be delivered within milliseconds.
- Calls should have minimal latency.
- Fast media uploads and downloads.

---

## Security

- Protect personal user data.
- End-to-End Encryption (E2EE) for messages and calls.
- Secure authentication.
- Encrypted data transmission using HTTPS/TLS.

---

## Reliability

- No message loss.
- Messages should eventually be delivered even if the receiver is offline.
- Automatic retries for failed message delivery.
- Backup and recovery support.

---

## Availability

- Service should be available 24×7.
- High uptime (e.g., 99.99% availability).
- Continue working even if some servers fail.

---

## Storage & Data Access

- Access local media stored on the device.
- Efficient cloud backup (optional).
- Fast retrieval of chat history.

---

## Integration

The application should integrate with:

- External websites
- Maps
- Phone contacts
- Camera
- Gallery
- Microphone
- Bank accounts / UPI apps (for payments)

---

## Automatic Operations

- Status automatically disappears after **24 hours**.
- Messages deleted using **Delete for Everyone** should disappear for all participants (subject to platform rules and time limits).

---

## Fault Tolerance

The system should continue working even if:

- One server crashes.
- A database replica fails.
- A network path becomes unavailable.

---

# Functional vs Non-Functional Examples

| Functional Requirement | Corresponding Non-Functional Requirement |
|-------------------------|------------------------------------------|
| Send messages | Messages should be delivered in **<100 ms** (target) |
| Make voice calls | Low latency and high audio quality |
| Upload status | Status should be available globally with minimal delay |
| Send media | Fast upload/download even for large files |
| WhatsApp Payments | Secure, encrypted, and reliable transactions |

---

# Architecture Impact

Each requirement influences the system architecture.

| Requirement | Possible Design Component |
|-------------|---------------------------|
| Send messages | Messaging Server |
| Store chats | Database |
| Fast message delivery | Cache |
| Millions of users | Load Balancer + Horizontal Scaling |
| Media sharing | Object Storage + CDN |
| Offline messages | Message Queue |
| End-to-End Encryption | Cryptographic Services |
| Reliability | Database Replication |
| High Availability | Multiple Servers + Failover |

---

# Key Takeaway

When designing WhatsApp, always separate requirements into two categories:

## Functional Requirements (What?)

- Login
- Messaging
- Calling
- Status
- Payments
- Contact Management
- Media Sharing

## Non-Functional Requirements (How Well?)

- Scalability
- Performance
- Security
- Reliability
- Availability
- Fault Tolerance
- Low Latency
- End-to-End Encryption

> **Correction to the original notes:**  
> A few items like **"Remove status after 24 hours"** and **"Delete message for everyone"** were listed as non-functional requirements. These are actually **functional requirements**, because they describe **specific system behaviors/features**, not quality attributes. Non-functional requirements describe qualities such as performance, scalability, security, and reliability.
