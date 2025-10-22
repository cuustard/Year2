Noted: 07/10/2025 #week1

> [!info] Resources
> [📊 PowerPoint](WK1.LC1.Data_Engineering_And_Databases.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=11692c2d-f819-4298-8cce-b36300370fb8)
> [📽️Lecture Recording Prt 2](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=7e94d17c-ce2a-44f4-8bf3-b36300371bed)

```table-of-contents

```
---
## The YouTube video linked below is *very* useful for this lecture/topic (Channel is useful for the whole module). 

[Keys](https://www.youtube.com/watch?v=8wUUMOKAK-c)
[Entity Relationships](https://youtu.be/LowjDtiNlk4?si=Pon3Y_UJkKbveHW_)

---
## Understanding Data
### Definition
**Data** is any information that can be represented in **binary form** (0s and 1s).
	```Examples: text, images, sound, numbers—all can be encoded digitally. ```
### Sources of Data
Data is constantly generated during activities such as:
	```Eating, travelling, chatting, calling, gaming, etc.```
### Purpose of Data
The goal of collecting data is to **retrieve information**.
To process data effectively, it must have a **common**, **flexible**, and **understandable representation**.

---
## What is Data Engineering?

### Definition #keyTermDefinition
```
Data Engineering is the process of designing and building systems that collect, manage, and analyse data to make it usable for business insights and decision-making.
```
### Key Responsibilities of Data Engineers
- **Data Pipelines:** Build and manage data flows for processing large datasets.
- **Data Integration:** Combine data from multiple sources seamlessly.
- **Data Quality:** Maintain reliability, consistency, and performance.
- **Data Analysis:** Prepare raw data for predictive modelling and trend analysis.
- **Data Security:** Protect data from unauthorized access, loss, or theft.
- **Automation:** Streamline repetitive processes in the data pipeline.
### Common Tools & Technologies
- Hadoop
- MongoDB
- Kafka
- Spark
- SQL-based systems
---
## Databases
### Definition #keyTermDefinition
```
A database is a structured system for storing, retrieving, and managing data efficiently.
```

Common examples: 
- **MySQL**
- **PostgreSQL**
- **Oracle**
- **MongoDB**
### Key Features
- Stores **raw data** before processing.
- Organizes data using **data models** to define structure and relationships.
- Ensures **efficient queries**, **fast access**, and **secure storage**.
- Must scale with increasing data volume (both on-premises and cloud-based).
---

## Why Database Management Systems (DBMS)?
### Before DBMS
Data was stored in **file-processing systems**:
- Difficult to optimize, reuse, or standardize.
- Low reliability and performance.
### DBMS Benefits
- Offers **efficient**, **reliable**, **multi-user**, and **secure** access to large datasets.
- Similar in purpose to an operating system—provides standardized data management.
---
## Relationship Between Data, Database, and DBMS

|Concept|Description|
|---|---|
|**Data**|Raw binary information.|
|**Database**|Structured collection of persistent data, organized by a **logical model**.|
|**DBMS**|Software managing databases—handles storage, retrieval, and security.|
|**Logical Model**|Conceptual design defining how data is represented (via **UML** or **ER diagrams**).|

---
## Entity Relationship (ER) Diagrams

### Purpose
- To represent **business rules** and **database structure** graphically.
- Used for documentation, debugging, and database maintenance.
### Example
Business Rule:
```
Every _Agent_ must have exactly one _AgentType_, but each _AgentType_ can relate to multiple _Agents_.
```

This is represented in an ER diagram with a **one-to-many relationship (1:N)** between _AgentType_ and _Agent_.
![[Pasted image 20251018165145.png]]

---
## ER Diagram Key Concepts
### Entities and Attributes
- **Entity:** A distinct object with identifiable attributes (e.g., _Car_, _Agent_, _Customer_).
- **Attributes:** Characteristics of an entity (e.g., _Model_, _Weight_, _Max_Speed_).
#### Notation
- **Rectangle:** Entity
- **Oval:** Attribute
- **Underline:** Primary Key
- **Dashed Oval:** Derived attribute
- **Double Oval:** Multi-valued attribute
- **Group of Attributes:** Composite attribute
#### Key Attributes
- Identify entities uniquely within an entity set.
- **Primary Key:** Main identifier chosen by the designer.
#### Example
**Entity Set:** Car  
**Attributes:** Model (Primary Key), Weight, Length, Max_Speed  
**Derived Attribute:** Max_Kinetic_Energy (computed)  
**Multi-valued Attribute:** Pre_Owners
![[Pasted image 20251018165303.png]]

---
## Relationships
### Definition #keyTermDefinition
```
- A relationship represents associations between two or more entities.
- Comes directly from business rules.
```
### Notation
- **Diamond:** Relationship set (e.g., _Repairs_ between _Mechanic_ and _Car_).
- **Lines:** Connect entities to relationships.
### Types by Degree
- **Unary:** Relationship within one entity set (e.g., _Employee supervises Employee_).
- **Binary:** Relationship between two entities (most common).
- **Ternary:** Relationship among three entities (e.g., _Customer borrows Loan from Branch_).
---

## Cardinalities (Mapping Constraints)
### Definition #keyTermDefinition
```
- Specifies how many entities in one set are associated with entities in another set.
- Derived from business rules.
```
### Types

| Cardinality            | Description                             | Example                                   |
| ---------------------- | --------------------------------------- | ----------------------------------------- |
| **1:1 (One-to-One)**   | Each entity in A relates to one in B.   | Marriage (Husband–Wife)                   |
| **1:N (One-to-Many)**  | One entity in A relates to many in B.   | _AgentType_ → _Agents_                    |
| **N:1 (Many-to-One)**  | Many entities in A relate to one in B.  | _Cars_ repaired by a single _Mechanic_    |
| **M:N (Many-to-Many)** | Many entities in A relate to many in B. | _Students_ enrolled in multiple _Courses_ |

---
## Core Database Languages and Roles

### Languages
- **DDL (Data Definition Language):** Defines structure (CREATE, ALTER, DROP tables).
- **DML (Data Manipulation Language):** Manages data (INSERT, UPDATE, DELETE).
### Roles in Database Systems
- **DBMS Implementer:** Builds and maintains DBMS software.
- **Database Designer:** Defines schema and structure.
- **Application Developer:** Builds software that interacts with databases.
- **Database Administrator (DBA):** Manages, secures, and tunes the database.
---