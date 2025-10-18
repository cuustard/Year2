Noted: 10/10/2025 #week1

> [!info] Resources
> [📊 PowerPoint](WK1.LC2.System_Design.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=d89e6356-29fa-4dbb-b616-b36600e33d08)

```table-of-contents

```

---
## What System Design Is

System design is all about optimisation, bottlenecks, constraints, resources, and metrics. System design patterns consists of multiplexing, pipelining, batching, locality/caching, distributed/hierarchy, abstraction/binding and indirection, virtualisation/randomisation, data and control separation. CUM

A system is a collection of components including hardware and software that work together to achieve a specific goal. Therefore, **System Design** is the science of putting together resources into a harmonious whole. #keyTermDefinition

In real life, we can't always quantify and control all systems metrics. Metrics like scalability, modularity, extensibility, and elegance are essential but unquantifiable. Rapid technological change can add ore remove resource constraints. For example, multi-core CPUs can overcome the limitations of CPU clock speed, but need a rethink for application architectures. Moreover, market conditions may dictate changes to the design halfway through the process.

---
### System Optimisation

In a system, some resources are more freely available than others. For example, a high-end PC connected to the internet via a a busy Wi-Fi connection. The bandwidth is a constrained resource while the entire PC and all it's hardware is unconstrained.

An optimised system is the max set of performance metrics given a set of resources constraints. #keyTermDefinition  Identifying metrics, resources, and constraints, aids in designing efficient systems.

#### Common Resources

- **Time**: could be fore multiple aspects
	- Deadline for task completion
	- Time to market
	- Mean time between failures
- **Space**: Shows up as
	- Number of PCI slots
	- Limit to available memory
	- Bandwidth
- **Computation**: Amount of processing that can be done in unit time
	- Can increase computing power by using more processors or waiting for a while
- **Cost**: to implement 
	- what components can be used
	- what price users are willing to pay for a service
	- the number of engineers available to complete a task.
- **Labour**: human effort required to design and build a system
	- Constraints what can be done, and how fast

---
### System Constraints

#### Scaling

The ability of a system to handle an increasing amount of work, users, or data by adding resources **without a proportional loss of performance** #keyTermDefinition. Scaling is a **design constraint** rather than a system constraint, but it has a major impact on the system’s overall feasibility and success.

**Key Points:**
- Hard to measure but crucial for system success.
- Often requires **distributed system design** and **complex coordination algorithms**.
- Centralised components can become bottlenecks.
- Technically a *design constraint*, but it strongly impacts the system’s overall feasibility.

#### Social

**Social Standards**: These are external [[Software Requirements|requirements]] or conventions that systems must conform to, even if they do not always make technical sense. Under-specified or inconsistently applied standards can lead to **faulty** or **non-interoperable implementations**.

**Social Market Requirements**: Market and user expectations can impose additional design constraints, such as:
- **Backward compatibility** with older systems or products.
- Dependence on a **specific operating system** or platform.

#### Resilience

Resilience is the ability of a system to continue operating correctly, or recover quickly, when it faces unexpected problems such as hardware failures, software bugs, high load, or cyberattacks. This includes quantitative (availability) and qualitative aspects (safety). Typically, resilience depends on risk analysis/threat model to understand constraints.

---
### System Metrics

| Category                                         | Goal/What It Measures                              | Typical Metrics                                                                                         |
| ------------------------------------------------ | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Performance/Efficiency                           | System speed/responsiveness                        | **Latency** (response time)<br>**Throughput** (ops/sec)<br>**Utilisation** (CPU, link)                  |
| Scalability                                      | How performance changes with workload or resources | **Elasticity** (load adaptation)<br>**Parallel Efficiency**                                             |
| Reliability/Availability/<br>Resilience/Security | Ability to function despite failures               | **Mean Time Between Failures**<br>**Availability = Uptime/(Uptime+Downtime)**<br>**Isolation Strength** |
| Cost/Resource utilisation                        | Efficiency in using limited resources              | **CapEx / OpEx- Memory / Network Bandwidth Usage**                                                      |
| Maintainability/Evolvability                     | Ease of modification, debugging, or scaling        | **Code Complexity (LOC, Cyclomatic)**<br>**Deployment Time - Configuration Overhead**                   |
| Sustainability                                   | Environmental, power, and material impact          | **Energy Per Operation**<br>**Carbon Footprint** (CO<sub>2</sub>)                                       |

---
## System Bottlenecks

The bottleneck of a system is an element that is the most constrained with respect to our optimisation. #keyTermDefinition. Performance metrics improves by removing the bottleneck but this can create a new bottleneck. In a balanced system, all resources are simultaneously bottlenecked. This is optimal but near impossible to achieve. 

![[Pasted image 20251018121259.png]]

---
## System Design Patterns

Not all system metrics can be easily quantified or controlled. Qualities such as scalability, modularity, extensibility, and elegance are essential but often unmeasurable.

Rapid technological change can introduce or remove resource constraints.
- For example, multi-core CPUs help overcome the limits of clock speed but require rethinking application architectures.

Market conditions may also force changes to system design during development.  
Nevertheless, it remains possible to identify guiding principles, such as:

- **Use unconstrained resources to alleviate bottlenecks.**

---
## Multiplexing

Using a single resource to handle multiple requests simultaneously (i.e., sharing) without interference.

**Goal:** Serve many users efficiently without significantly increasing resource requirements.
- Useful for managing cost constraints.
- Users may experience increased response times and waiting periods, but overall system costs are reduced due to economies of scale.

#### Multiplexing Dimensions

- **Time** – _CPU and I/O multiplexing_
    - Multiple processes share the CPU and access the same disk.
    - The OS scheduler ensures that processes do not interfere with each other.

- **Space** – _Memory multiplexing_
    - Virtual memory provides each process with its own address space.

- **Frequency** – _Radio communications_
    - Mobile networks use the same airwaves to transmit signals.
    - Advanced algorithms leverage multiple frequencies to support more users without degrading performance or resilience.

#### Statistical Multiplexing

- Resources are **shared dynamically** based on demand.
- Suppose a resource has capacity **C**.
    - It is shared by **N** identical tasks.
    - Each task requires capacity **c**.
- If **N c ≤ C**, the resource is underloaded.
- If at most **10% of tasks are active**, then it is sufficient for **C ≥ N c / 10**.
- We use **statistical knowledge of user behaviour** to reduce system cost.
- The efficiency gained through this probabilistic sharing is known as the **statistical multiplexing gain**.

####  Statistical Multiplexing Gain Example

```
Consider a 100-room hotel deciding how many external phone lines to rent. Each line costs money to install and maintain, so providing one per room is wasteful. If a voice call is active only 40% of the time, the hotel could rent around 40 lines instead of 100. However, if more than 40 guests call simultaneously, some calls will be blocked, reducing user satisfaction.

Accurate statistical data on resource usage is crucial to balance cost efficiency and service quality. If usage patterns or statistics are incorrect or change over time, performance suffers. The same principle applies to road systems, where incorrect demand estimates lead to either congestion or underused capacity.
```

![[Pasted image 20251018121239.png]]

---
## Pipelining

- Increases **throughput** (tasks completed per unit time) but does not necessarily reduce **latency** (time to complete a single task).
- Technique to complete a task faster by dividing it into smaller **subtasks**.
- Effective when tasks can be split into **independent or partially dependent stages**.
- **Optimal** when all subtasks take **similar amounts of time**.

*Example*:
```
Web browsers downloading multiple page elements concurrently.
```

#### Dependent Subtasks

- Some tasks cannot start until others finish (e.g., steps in **cooking**).
- Adding more processors **does not always improve performance** in these cases.

#### Pipelining Concept

- Special case of dependent tasks where each stage depends **only on the previous one**.
- Tasks arranged in a **sequence of stages** (like an **assembly line**).
- Each processor works on a **different stage simultaneously**, enabling **overlapping execution** — while one stage finishes, the next begins.

![[Pasted image 20251018121223.png]]

---
## Batching

Batching involves grouping tasks together and processing them as a single unit rather than handling them individually. This approach **amortizes overheads** for example, loading time or setup costs and is effective when the overhead for **N tasks** is less than **N times the overhead for a single task** (i.e., a nonlinear relationship).

For instance, if loading two 16-bit instructions takes the same time as loading one 16-bit instruction, read access times are improved. However, the time taken to **accumulate a batch** should not be too long, as this increases the **worst-case response time**. Overall, batching **trades slightly longer individual response times for higher throughput**, improving **average system response** and allowing the CPU to **complete more instructions per second**.

![[Pasted image 20251018121211.png]]

---
## Exploiting Locality

Exploiting locality leverages the observation that if a system accesses some data at a given time, it is likely to access the **same or nearby data soon**.

- **Spatial locality** refers to accessing **nearby data**, such as watching consecutive episodes on a streaming service.
- **Temporal locality** refers to accessing **recently used data again soon**, such as the next instruction in a program.

By exploiting locality, systems can **improve access times** and **reduce load** on slower resources or paths to the main server.

**Caching** is a common implementation: frequently accessed data from larger, slower storage is stored in **smaller, faster storage**.

- Example: **Filesystem caching** provides the speed of RAM while maintaining the capacity of disk storage.

![[Pasted image 20251018121157.png]]

---
### Hierarchy

Hierarchy involves the **recursive decomposition** of a system into smaller components, where each piece depends only on its **parent** for correct operation.

- **Examples:** computer memory organization, network addressing.
- **Characteristics:**
    - No single point of control.
    - Highly **scalable**.
    - **Leaf-to-leaf communication** can be expensive, but **shortcuts** (e.g., direct links) can help reduce cost.

![[Pasted image 20251018120542.png]]

---
### Binding And Indirection

- **Abstraction** enables generality in system design (e.g., domain names, variable pointers).
- **Binding** translates an abstraction into a concrete instance.
- **Indirection** uses a reference to access something instead of accessing it directly.
    - Provides **flexibility**, as the reference can change without affecting the higher-level system.
- **Dynamic binding** allows optimization for current conditions.
    - Example: using a domain name to access the **closest instance** of a service.
    - Common on the Internet, enabling users to be directed to the **best server** based on current load or location.

---
## Virtualisation

- Combines **indirection** and **multiplexing** to create a **virtual version of a resource** (hardware, OS, network, or storage).
- Allows multiple **independent systems or applications** to share the resource as if each has its **own dedicated instance**.

**Examples:**
- Virtual memory
- Virtual modem
- Cloud computing

Enables **clean and dynamic system reconfiguration** by simplifying programming for developers, allowing code to run **without worrying about synchronization** with other programs.

---
## Randomisation

Used to **break ties fairly** and as a simple method to **spread load**.

**Examples:**
- Resolving contention in a broadcast medium.
- Using **hashes on load balancers** to distribute traffic across backend servers.

**Statistics are important**: if tasks require different amounts of effort, fairness can be compromised.

![[Pasted image 20251018121136.png]]

---
### Separating Data And Control

- Divides system actions into:
    - **Control plane**: actions that happen once per data transfer (rules, scheduling, routing).
    - **Data plane**: actions that occur once per packet (payload, instructions, user content).

- Benefits:
    - **Throughput improvement** by optimizing processing in the data path.
    - **Enhanced intelligence** by separating decision-making from actual data handling.

**Example:** Software-defined networks (SDNs).

Trade-off: keeping some control information in the data plane can allow **per-packet optimization**, such as Quality of Service (QoS).

![[Pasted image 20251018120957.png]]

---
## Performance Analysis And Tuning

Use system design techniques to **tune existing systems** for better performance.

- **Steps:**
    1. **Measure**: collect performance data from the system.
    2. **Characterize workload**: understand the patterns and demands on the system.
    3. **Build a system model**: create an abstract representation of the system to predict performance.
    4. **Analyse**: identify bottlenecks and opportunities for improvement.
    5. **Implement**: apply changes and optimizations based on analysis.

---
