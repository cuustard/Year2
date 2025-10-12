Noted: 10/10/2025 #week1

> [!info] Resources
> [📊 PowerPoint](SystemDesign.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=d89e6356-29fa-4dbb-b616-b36600e33d08)

```table-of-contents

```

---
## What System Design Is

System design is all about optimisation, bottlenecks, constraints, resources, and metrics. System design patterns consists of multiplexing, pipelining, batching, locality/caching, distributed/hierarchy, abstraction/binding and indirection, virtualisation/randomisation, data and control separation. CUM

A system is a collection of components including hardware and software that work together to achieve a specific goal. Therefore, **System Design** is the science of putting together resources into a harmonious whole. #keyTermDefinition

In real life, we can't always quantify and control all systems metrics. Metrics like scalability, modularity, extensibility, and elegance are essential but unquantifiable. Rapid technological change can add ore remove resource constraints. For example, multi-core CPUs can overcome the limitations of CPU clock speed, but need a rethink for application architectures. Moreover, market conditions may dictate changes to the design halfway through the process.

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


### System Constraints

#### Scaling

The ability of a system to handle an increasing amount of work, users, or data by adding resources **without a proportional loss of performance** #keyTermDefinition. Scaling is a **design constraint** rather than a system constraint, but it has a major impact on the system’s overall feasibility and success.

**Key Points:**
- Hard to measure but crucial for system success.
- Often requires **distributed system design** and **complex coordination algorithms**.
- Centralised components can become bottlenecks.
- Technically a *design constraint*, but it strongly impacts the system’s overall feasibility.

#### Social

**Social Standards**: These are external requirements or conventions that systems must conform to, even if they do not always make technical sense. Under-specified or inconsistently applied standards can lead to **faulty** or **non-interoperable implementations**.

**Social Market Requirements**: Market and user expectations can impose additional design constraints, such as:
- **Backward compatibility** with older systems or products.
- Dependence on a **specific operating system** or platform.

#### Resilience

Resilience is the ability of a system to continue operating correctly, or recover quickly, when it faces unexpected problems such as hardware failures, software bugs, high load, or cyberattacks. This includes quantitative (availability) and qualitative aspects (safety). Typically, resilience depends on risk analysis/threat model to understand constraints.
### System Metrics

| Category                                         | Goal/What It Measures                              | Typical Metrics                                                                                         |
| ------------------------------------------------ | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Performance/Efficiency                           | System speed/responsiveness                        | **Latency** (response time)<br>**Throughput** (ops/sec)<br>**Utilisation** (CPU, link)                  |
| Scalability                                      | How performance changes with workload or resources | **Elasticity** (load adaptation)<br>**Parallel Efficiency**                                             |
| Reliability/Availability/<br>Resilience/Security | Ability to function despite failures               | **Mean Time Between Failures**<br>**Availability = Uptime/(Uptime+Downtime)**<br>**Isolation Strength** |
| Cost/Resource utilisation                        | Efficiency in using limited resources              | **CapEx / OpEx- Memory / Network Bandwidth Usage**                                                      |
| Maintainability/Evolvability                     | Ease of modification, debugging, or scaling        | **Code Complexity (LOC, Cyclomatic)**<br>**Deployment Time - Configuration Overhead**                   |
| Sustainability                                   | Environmental, power, and material impact          | **Energy Per Operation**<br>**Carbon Footprint** (CO<sub>2</sub>)                                       |

### System Bottlenecks

The bottleneck of a system is an element that is the most constrained with respect to our optimisation. #keyTermDefinition. Performance metrics improves by removing the bottleneck but this can create a new bottleneck. In a balanced system, all resources are simultaneously bottlenecked. This is optimal but near impossible to achieve. 

---
## System Design Patterns

#doitlater 


### Multiplexing


### Pipelining


### Batching


### Locality


### Hierarchy


### Binding And Indirection


### Virtualisation/Randomisation


### Separating Data And Control


---
## Performance Analysis And Tuning

