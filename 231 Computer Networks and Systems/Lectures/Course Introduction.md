Noted: 06/10/2025 #week1

> [!info] Resources
> [📊 PowerPoint](CourseIntroduction.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=b505e5ce-51eb-4587-875c-b363003733b6)

> [!info] Required Reading
> [📘 Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)
> [📘 Computer Networking: A Top-Down Approach](https://bit.ly/2FunP0a)
> 

```table-of-contents

```
---


The module aims to instil a deep understanding of how **computer operating systems and networks interact** to enable the distributed applications ubiquitous today. It also provides knowledge and practical experience in **internet architecture, network protocols, and operating system principles**, as expected of all computer science graduates.

Term 1 Topics:
- **System Design**
- **Operating Systems**
- **Internet Protocol Stack**
- **Application Layer**
- **Transport Layer**
- **Network Layer**
- **Link Layer**
- **Cloud**

Term 1 Labs:
- Processes APIs in the Linux Kernel
- Introduction to Systems Programming (**IPC**)
- Intro to network monitoring and testing
- Building a network application / Intro to **Mininet**
- Coursework support
- Configuring an **OSPF network**
- Coursework submission

Assessment:
- **Python** is the focus for this year
- **Exam:** 70% (Summer term)
    - Any lecture or lab topic may appear in the final exam unless explicitly stated otherwise
- **Coursework:** 30%
    - Network application development split into weekly parts


A **system** is a collection of hardware and/or software components whose interactions enable them to work together to achieve a goal. #keyTermDefinition 

A **Systems Engineering** is a discipline of designing, integrating, and managing complex systems throughout their lifecycle. #keyTermDefinition 

---
## The Operating System

An [[Virtualisation And The Operating System#The Operating System|Operating System]] (OS) is a software layer that sits between computer hardware and user applications. It manages hardware resources such as the CPU, memory, and devices, and provides services like scheduling, device drivers, and inter-process communication through pipes, message queues, shared memory, and signals. By doing this, it allows multiple processes to share resources safely and offers convenient abstractions for running applications. #keyTermDefinition 

The building blocks of OS's are Virtualisation, Concurrency, Persistence, and Security.

---
## The Network / Internet

The **Internet** is a global network of interconnected hosts, packet switches, and communication links that enables end-to-end data transfer between processes using standardized protocols to support distributed applications and services. #keyTermDefinition 

The internet has physical connections like links and interfaces. Communication is done across machines via sockets & protocols. There is end-to-end data transfer via logical channels between processes. 

The internet has 3 main components:
- **Communication Links**: Includes fiber, copper, radio, and satellite connections. They carry data across the network, and their **bandwidth** determines the transmission rate.
- **Packet Switches**: Forward packets of data through the network, using devices such as routers and switches to determine the best paths.
- **Hosts**: These are the billions of connected computing devices running network applications at the internet’s edge.

The internet is an infrastructure that provides services to distributed applications like the web, e-mail, games, etc. The Internet is a network of networks. Protocols send and receive messages and protocol standards ensure standard delivery of data. A protocol defines the format, order of data exchanged among network entities, and actions, to be taken on message transmission/receipt/non-receipt.

---
## The Cloud

Entire server clusters and virtual machines and containers


#doitlater 

