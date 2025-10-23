> [!info] Resources
> [[WK2.WKSP1.Use_Cases.pdf|⚒️ Workshop Task]]

```table-of-contents
```
---
## Recap: Use Case Diagram

![[Pasted image 20251023122840.png]]
- The primary actor in the bank customer whose intention is to achieve one or more than 3 the goals described represented by use cases (show in blue).
- The customer account database is a secondary actor helping the customer to achieve their goal.
- All the 3 use cases require the customer to be verified. This implies that customer verification is common behaviour in the three use cases. We can extract and represent it it using the `<<include>>` keyword (see "red" use-case).

![[Pasted image 20251023122914.png]]

### `<<include>>` And `<<extend>>` Relationship

There may be use cases that share common or mandatory behaviour.
- Common or shared behaviour is represented using the `<<include>>` relationship, represented with a broken arrow that points from the use case that requires the behaviour ..... to the shared use case.

There are cases where a use case may conditionally add steps to another use case. For example optional behaviour.
- This behaviour can be modelled using the `<<extend>>` relationship
- Optional or alternative behaviour is depicted using a broken arrow, draw from the alternate/optional use case to the use case that it extends.


### Guidelines For Writing Use Cases

- To identify the right use cases, always keep in mind the **goal** that the actor wants to achieve by using the system.
	- What **task(s)** do you want the system to help you achieve?
- Avoid excessive use structuring
	- Remember use cases are about communicating high-level system behaviour not low-level implementation detail
	- Avoid functional decomposition. High-level use cases cannot de decomposed into lower-level use cases.
	- a use case can **only** by linked to another use via an `<<include>>` or `<<extend>>` relationship. **Never** directly.

## Task: Conference Paper Review System

### The Problem

Scientific conferences are held to announce and discuss new results and ideas. The core activity of organising a conference centres on selecting interesting research to be presented. This is done by via an open invitation calling for papers to be submitted and setting up a (geographically distributed) panel of reviewers. Submitted papers are then circulated to the reviewers who select the best papers to appear on the programme. 

An automated system is needed to support the paper reviewing process as follows:

1. Authors submit papers to the system. A paper submission must be accompanied by authors' affiliation details. The program char (PC) of the conference checks the validity of submitted papers and assigns each valid paper a unique number. Invalid submission are rejected at this point and the authors informed. After the paper submission deadline, the PC uses the system to distribute valid submitted papers among the reviewers. Each paper is sent to three distinct reviewers, none of whom is an author of the paper.
2. The reviewers submit their reviews to the system before an agreed deadline.
3. The PC notifies the authors about the review results.
4. Authors of accepted papers submit revised final version papers. The PC checks that the re-submitted papers have taken into account reviewer comments.

### The Task

Use PlantUML.

1. Draw a use-case diagram for the conference paper reviewing system
2. Suggest 2 possible [[WK1.LC1.Software_Requirements#Types of Requirements And Metrics for Measuring|non-functional requirements]] the conference reviewing system
3. A PlantUML example is provided in the next slide

### Our Answer