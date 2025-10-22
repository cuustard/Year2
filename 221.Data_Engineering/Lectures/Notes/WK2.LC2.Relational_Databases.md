noted: #week2 

> [!info] Resources
> [📊 PowerPoint](WK2.LC2.Relational_Databases.pdf)
> [📽️Lecture Recording]()

```table-of-contents
```
---
## The YouTube video linked below is *very* useful for this lecture/topic (Channel is useful for the whole module). 

[Keys](https://www.youtube.com/watch?v=8wUUMOKAK-c)
[Entity Relationships](https://youtu.be/LowjDtiNlk4?si=Pon3Y_UJkKbveHW_)

---
## Relational Model Overview

The **Relational Model** represents data as **relations (tables)**. #keyTermDefinition 

Each table (relation) consists of:
- **Attributes (columns):** Describe entity properties.
- **Tuples (rows):** Individual data records.

A relation is essentially a **set of tuples** with no duplicates.
Each attribute has a defined **domain** (set of allowable values).

**Example:**
```
STUDENT (StudentID, Name, Course, Year)
```

---
## Structure and Terminology

|Concept|Description|
|---|---|
|**Relation**|Table of data|
|**Tuple**|Row (record)|
|**Attribute**|Column (field)|
|**Domain**|Allowed data type for an attribute|
|**Degree**|Number of attributes in a relation|
|**Cardinality**|Number of tuples (rows)|

---
## Keys in a Relation

Keys ensure **uniqueness** and **integrity** within tables.
### Types of Keys

- **Super Key:** Any attribute (or set) that uniquely identifies tuples.
- **Candidate Key:** Minimal super key (no redundant attributes).
- **Primary Key:** Selected candidate key used as the main unique identifier.
- **Alternate Key:** Candidate keys not chosen as primary.
- **Foreign Key:** Attribute linking one table to another’s primary key.
    - Enforces **referential integrity**.

**Example:**
```
STUDENT(StudentID, Name, CourseID)
COURSE(CourseID, Title)
→ COURSE.CourseID = STUDENT.CourseID (Foreign Key)
```

---
## Integrity Constraints

Integrity constraints preserve **validity and consistency** in the database.
### Types

1. **Domain Constraint**
    - Attribute values must lie within a defined domain.
    - Example: `Age` must be an integer between 0–120.
2. **Entity Integrity**
    - Primary key values **cannot be NULL**.
3. **Referential Integrity**
    - Ensures that foreign key values must **match** existing primary key values in the referenced table or be **NULL**.
4. **Key Constraint**
    - No two tuples can have the same primary key value.

---
## Relationships in Relational Databases
Relationships define how tables (relations) connect to each other.

|Type|Description|Example|
|---|---|---|
|**1:1**|One entity in A corresponds to one in B|Each _Employee_ has one _Locker_|
|**1:N**|One entity in A maps to many in B|One _Department_ has many _Employees_|
|**N:M**|Many in A relate to many in B|Many _Students_ take many _Courses_|
**Implementing Relationships:**
- 1:N → Foreign key in the “many” table
- N:M → Use a **junction table** (bridge relation) with foreign keys to both entities

**Example:**
```
ENROLLMENT(StudentID, CourseID, DateEnrolled)
```

---
## Operations on Relations (Relational Algebra)
Fundamental operations allow manipulation of relational data.

|Operation|Description|
|---|---|
|**SELECT (σ)**|Filters rows based on condition|
|**PROJECT (π)**|Extracts specific columns|
|**UNION (∪)**|Combines tuples from two relations (duplicates removed)|
|**SET DIFFERENCE (−)**|Returns tuples in one relation but not the other|
|**CARTESIAN PRODUCT (×)**|Combines all tuples from two relations|
|**RENAME (ρ)**|Renames attributes or relations|
|**JOIN (⋈)**|Combines related tuples from two relations using common attributes|
**Example (JOIN):**
```
STUDENT ⋈ COURSE → merges both tables using CourseID
```

---
## Normalization (Brief Overview)

Normalization removes redundancy and ensures data consistency.

|Normal Form|Description|
|---|---|
|**1NF**|All attributes contain atomic (indivisible) values.|
|**2NF**|1NF + all non-key attributes depend on the whole primary key.|
|**3NF**|2NF + no transitive dependencies.|
**Goal:**  
```
Avoid anomalies (insertion, deletion, update) and maintain efficient structure.
```
### Example

**Tables:**
```
DEPARTMENT(DeptID, DeptName, ManagerID)
EMPLOYEE(EmpID, Name, DeptID)
```
- `DeptID` → Primary Key in DEPARTMENT
- `DeptID` in EMPLOYEE → Foreign Key referencing DEPARTMENT

**Meaning:**  
Each department can have many employees (1:N relationship).

---
## Advantages of the Relational Model

- Logical data independence
- Simple, table-based representation
- Strong theoretical foundation (set theory)
- Easier to query using SQL
- Supports powerful integrity enforcement and normalization
---
## Summary of Key Symbols (ER to Relational Mapping)

|ER Concept|Relational Representation|
|---|---|
|Entity|Table|
|Attribute|Column|
|Primary Key|Unique identifier|
|Relationship (1:N)|Foreign Key in N-side|
|Relationship (N:M)|Bridge table with two Foreign Keys|
|Weak Entity|Table with composite key (Owner PK + Weak Key)|

---