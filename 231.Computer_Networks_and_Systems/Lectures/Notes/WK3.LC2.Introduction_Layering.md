---
date: 2025-12-24
noted: false
tags:
---
```table-of-contents
```

> [!info] Resources
> [📊 PowerPoint]()
> [📽️Lecture Recording]()

---
## What is a Protocol?
### Definition
A **protocol** defines:
- The **format** and **order** of messages exchanged between network entities (hosts, routers, etc.)
- The **actions** taken when messages are sent, received, or lost.

Protocols ensure **interoperability** — essential in a massive distributed system like the Internet.
### Analogy

![[Pasted image 20251024013000.png]]
Human conversation vs. computer protocol:

**Key Point:**  
Both follow rules about message order and responses, this is the essence of a protocol.

---
## Internet Structure — A Network of Networks

- The Internet is a **global system of interconnected networks**.
- **Hosts** connect through **access ISPs (Internet Service Providers)**.
- Access ISPs must be interconnected so any two devices can communicate.
### Hierarchical Internet Structure

1. **Access networks:** local, home, enterprise, mobile.
2. **Regional ISPs:** connect multiple access networks.
3. **Tier-1 ISPs:** large, well-connected providers (e.g., AT&T, NTT, Level 3).
4. **Content provider networks:** e.g., Google, Facebook — operate private global networks that often bypass Tier-1 ISPs.

![[Pasted image 20251024013051.png]]
This forms a **complex, hierarchical “network of networks”**, driven by **economic and policy factors**.

---
## The Network Core

The **network core** is a **mesh of interconnected routers** responsible for moving data between hosts.

![[Pasted image 20251024013133.png]]
### Packet Switching

- **Hosts** break data into **packets**.
- **Routers** forward packets across multiple links from **source to destination**.
- Packets share network resources dynamically — efficient but may cause **congestion**.
### Two Core Functions

1. **Forwarding:**
    - Local action within a router.
    - Moves packets from **input link → output link** using a **forwarding table**.
2. **Routing:**
    - Global process that determines **end-to-end paths** for packets.
    - Implemented by **routing algorithms**.

![[Pasted image 20251024013210.png]]
![[Pasted image 20251024013221.png]]
![[Pasted image 20251024013230.png]]

---
## Switching Techniques
### Packet Switching (Store-and-Forward)

- Each router **receives** the full packet before forwarding it.
- Transmission delay per link = L/RL / RL/R, where
    - L = packet length (bits)
    - R = link rate (bps)
- **Processing delay:** time taken to examine and forward the packet header.
![[Pasted image 20251024013255.png]]
### Queueing
- Occurs when **arrival rate > transmission rate** of a link.
- Packets are stored temporarily in a **buffer**.
- If buffer fills, packets are **dropped (lost)**.

![[Pasted image 20251024013307.png]]
### Circuit Switching

- **Dedicated path** established between sender and receiver.
- **Resources reserved** along the route → guaranteed performance.
- Common in **telephone networks**.
- Inefficient for bursty data (resources idle when not in use).

![[Pasted image 20251024013329.png]]
#### Multiplexing Methods

- **FDM (Frequency Division Multiplexing):**  
    Each user gets a narrow frequency band continuously.
    ![[Pasted image 20251024013357.png]]
- **TDM (Time Division Multiplexing):**  
    Each user transmits in periodic time slots.
    ![[Pasted image 20251024013404.png]]

---
## Circuit vs. Packet Switching

|Aspect|Circuit Switching|Packet Switching|
|---|---|---|
|**Resource Allocation**|Fixed, pre-reserved|Dynamic, on-demand|
|**Performance**|Predictable, constant|Variable (depends on load)|
|**Efficiency**|Poor for bursty data|Excellent for bursty data|
|**Setup Time**|Requires setup|No setup (immediate transmission)|
|**Scalability**|Limited|Highly scalable|
#### Example:

1 Gbps link, users need 100 Mbps and are active 10% of the time.
- Circuit switching → only 10 users possible.
- Packet switching → ~35 users (with low chance of overload).

![[Pasted image 20251024013435.png]]

Packet switching is more efficient and flexible but less predictable — congestion control is essential.

---
## Abstraction and Layering
### Why Layering?

Layering simplifies **design, implementation, and maintenance** of complex systems:
- Each layer provides a **specific service**.
- Layers **rely on the layer below** and **serve the layer above**.
- Changes in one layer don’t affect others (modularity).

---

## Analogy: The Airline System

Layers in air travel:
1. Ticketing
2. Baggage handling
3. Gate management
4. Runway operations
5. Routing (flight path)

![[Pasted image 20251024013537.png]]
![[Pasted image 20251024013559.png]]
Each performs a function and relies on lower layers just like networking layers.

---
## Internet Protocol Stack

| Layer           | Function                             | Examples                      |
| --------------- | ------------------------------------ | ----------------------------- |
| **Application** | Provides network services to users   | HTTP, IMAP, SMTP, DNS         |
| **Transport**   | Process-to-process data transfer     | TCP, UDP                      |
| **Network**     | Routing and addressing               | IP, routing protocols         |
| **Link**        | Data transfer between adjacent nodes | Ethernet, Wi-Fi (802.11), PPP |
| **Physical**    | Transmission of bits                 | Cables, fiber, radio          |
**Data moves down** the stack at the sender → transmitted → **moves up** the stack at the receiver.
![[Pasted image 20251024013620.png]]

---

## Encapsulation

Each layer **adds its own header** around data before passing it to the next.

|Layer|Unit|Header|Example|
|---|---|---|---|
|Application|Message|—|“HTTP request”|
|Transport|Segment|Hₜ|TCP header|
|Network|Datagram|Hₙ|IP header|
|Link|Frame|Hₗ|Ethernet header|
**Analogy:** Russian nesting dolls, each layer wraps the one above.

![[Pasted image 20251024013721.png]]
![[Pasted image 20251024013735.png]]
At the destination, headers are **removed in reverse order**.

---
## Network Experimentation: Mininet

**Mininet** allows simulation of a real network on a single Linux system.
- Emulates **hosts, switches, links, and controllers**.
- Networks described in **Python**.
- Interactive CLI allows direct control of nodes.
- Replicates **all IP layers** in a test environment.
#### Example: Simple Topology

![[Pasted image 20251024013836.png]]

Used to explore **forwarding, routing, and encapsulation** in practice.

---
## Summary

- The Internet = a **network of networks**, built for interoperability.
- **Protocols** define communication rules and behaviors.
- **Packet switching** enables efficient, bursty communication but requires congestion control.
- **Circuit switching** guarantees quality but wastes resources.
- **Layering** abstracts network complexity into manageable parts.
- **Encapsulation** organizes data flow between layers.
- **Mininet** provides hands-on experience simulating these layers.

---