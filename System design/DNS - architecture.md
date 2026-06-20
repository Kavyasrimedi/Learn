# Domain Name System (DNS)

The **Domain Name System (DNS)** is often called the **Internet's Phonebook**.

Its primary job is to translate **human-readable domain names** (e.g., `google.com`) into **IP addresses** (e.g., `142.250.183.14`) that computers use to communicate.

---

# Why Do We Need DNS?

Humans remember names easily:

```text
google.com
amazon.com
chat.openai.com
```

Computers communicate using IP addresses:

```text
142.250.183.14
13.224.200.12
104.18.33.45
```

DNS acts as the translator between the two.

```text
google.com
      │
      ▼
     DNS
      │
      ▼
142.250.183.14
```

---

# How Does the Browser Know Which Website to Open?

When you type:

```text
www.google.com
```

The browser asks the DNS system:

> "What is the IP address of `www.google.com`?"

DNS returns the IP address, and the browser connects to that server.

---

# Why Can't Browsers Store Every Website's IP Address?

Suppose browsers stored the IP address of every website.

Problems:

- There are **hundreds of millions of registered domain names** (and the number keeps growing).
- The list would become extremely large.
- Websites frequently change their IP addresses.
- Keeping every browser updated would be nearly impossible.
- If one centralized list failed, the Internet would become unreliable.

Instead, DNS uses a **distributed and hierarchical architecture**.

---

# Domain Structure

Example:

```text
courses.unstop.com
```

Breaking it down:

```text
courses   .   unstop   .   com
   │             │          │
Subdomain      Domain      Top-Level Domain (TLD)
```

Another example:

```text
mail.google.com
```

- `mail` → Subdomain
- `google` → Domain
- `.com` → Top-Level Domain

---

# Machines Communicate Using IP Addresses

Computers cannot communicate using names.

Every communication happens using IP addresses.

Example:

```text
Browser
   │
   ▼
142.250.183.14
```

DNS simply helps convert names into IP addresses.

---

# DNS Architecture

The DNS lookup involves several components:

```text
User
 │
 ▼
Browser
 │
 ▼
ISP / Local DNS Resolver
 │
 ├──────────────► Root Server
 │                    │
 │                    ▼
 │              TLD Server (.com)
 │                    │
 │                    ▼
 │          Authoritative Name Server
 │                    │
 ▼                    ▼
 Returns Final IP Address
```

---

# Components of DNS

## 1. DNS Resolver

The DNS Resolver (usually provided by your ISP or a public DNS service like Google DNS or Cloudflare DNS) receives the DNS request from the browser.

Responsibilities:

- Checks local cache.
- If not found, queries DNS hierarchy.
- Returns the final IP address.

Examples:

- Google DNS → `8.8.8.8`
- Cloudflare DNS → `1.1.1.1`

---

## 2. Root Server

The Root Server does **not** know the IP address of every website.

Instead, it knows where the **Top-Level Domain (TLD)** servers are.

Examples of TLDs:

- `.com`
- `.org`
- `.net`
- `.gov`
- `.edu`
- `.in`
- `.uk`

### Notes

- There are **13 logical root server identifiers (A–M)** managed by different organizations around the world. Through Anycast, these are served by **hundreds of physical server instances globally**, not just 13 machines.
- The Root Server simply directs the resolver to the appropriate TLD server.

---

## 3. TLD (Top-Level Domain) Server

The TLD server manages a specific top-level domain.

Example:

For:

```text
google.com
```

The `.com` TLD server knows which **Authoritative Name Server** stores information for `google.com`.

It returns the address of that authoritative server.

---

## 4. Authoritative Name Server

This server contains the actual DNS records for a domain.

It finally returns:

```text
google.com
      │
      ▼
142.250.xxx.xxx
```

This is the IP address that the browser uses to connect to the website.

---

# Complete DNS Lookup Process

Suppose the user enters:

```text
www.google.com
```

### Step 1

Browser checks its own DNS cache.

If found:

```text
Return IP
```

Otherwise continue.

---

### Step 2

Browser asks the DNS Resolver.

---

### Step 3

Resolver asks the Root Server.

Root Server replies:

> "Ask the `.com` TLD server."

---

### Step 4

Resolver asks the `.com` TLD server.

The TLD replies:

> "Ask Google's Authoritative Name Server."

---

### Step 5

Resolver asks Google's Authoritative Name Server.

It replies:

```text
142.xxx.xxx.xxx
```

---

### Step 6

Resolver returns the IP to the browser.

---

### Step 7

Browser connects to the server.

```text
Browser
   │
   ▼
142.xxx.xxx.xxx
```

The website loads.

---

# DNS Caching

A full DNS lookup happens only the first time (or after cached entries expire).

After that, the result is cached.

Caching occurs at multiple levels:

- Browser Cache
- Operating System Cache
- DNS Resolver Cache

This makes future lookups much faster.

---

# Example

### First Visit

```text
Browser
   │
DNS Lookup
   │
Root
   │
TLD
   │
Authoritative Server
   │
Return IP
```

Time taken:

```
~50–200 ms
```

---

### Second Visit

```text
Browser
   │
Cache
   │
Return IP
```

Time taken:

```
A few milliseconds
```

---

# Common DNS Record Types

| Record | Purpose |
|---------|---------|
| **A** | Maps a domain to an IPv4 address |
| **AAAA** | Maps a domain to an IPv6 address |
| **CNAME** | Alias for another domain |
| **MX** | Mail server records |
| **TXT** | Verification and security information |
| **NS** | Specifies the authoritative name servers |

---

# Key Takeaways

- DNS stands for **Domain Name System**.
- It translates **domain names** into **IP addresses**.
- Computers communicate using IP addresses, not names.
- DNS uses a **hierarchical architecture**:
  - DNS Resolver
  - Root Server
  - TLD Server
  - Authoritative Name Server
- Results are cached to reduce lookup time.
- The Root Server does **not** know every website's IP; it only directs queries to the appropriate TLD server.
- The Authoritative Name Server provides the final IP address for the requested domain.