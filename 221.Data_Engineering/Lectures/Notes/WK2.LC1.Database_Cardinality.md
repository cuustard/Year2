#week2 

> [!info] Resources
> [📊 PowerPoint](WK2.LC1.Database_Cardinality.pdf)
> [📽️Lecture Recording]()

```table-of-contents
```
---
## The YouTube video linked below is *very* useful for this lecture/topic (Channel is useful for the whole module). 

[Entity Relationships](https://youtu.be/LowjDtiNlk4?si=Pon3Y_UJkKbveHW_)

---
## Relationship Types

Cardinality defines how many entities in one set can be associated with entities in another set. #keyTermDefinition 

|Type|Description|Example|
|---|---|---|
|**1:1 (One-to-One)**|One entity in A relates to one entity in B|One mechanic repairs one car|
|**1:N (One-to-Many)**|One entity in A relates to many in B|One mechanic repairs many cars|
|**N:1 (Many-to-One)**|Many in A relate to one in B|Many cars repaired by one mechanic|
|**N:M (Many-to-Many)**|Many in A relate to many in B|Many mechanics repair many cars|

- “1” = one
- “N” = many
- “M” = many

**Always read the direction carefully.**

---
## Example – Works_In (Employees–Departments)

**Case 1:**
- An employee works in _at most one department_
- A department has _many employees_  
    → **1:N (One-to-Many)** relationship
**Case 2:**
- An employee works in _several departments_
- A department has _many employees_  
    → **N:M (Many-to-Many)** relationship

---
## Participation Constraints
Define whether **all** entities in one set participate in a relationship.

|Type|Description|Notation|
|---|---|---|
|**Total Participation**|Every entity _must_ participate in the relationship|**Double line**|
|**Partial Participation**|Some entities _may not_ participate|**Single line**|
### Examples

**Example 1:**
- Each _car_ must be repaired by at least one mechanic.
- Each _mechanic_ repairs exactly one car.  
    → Total participation on both sides.

**Example 2:**
- A car may be repaired by several mechanics.
- Each mechanic must repair exactly one car.  
    → Total participation for Mechanic, partial for Car.

---

## Employees–Departments Relationships
### Manages
- An employee can manage **at most one department**
- A department can be managed by **zero or one employee**  
    → **1:1** relationship
- Exactly one employee must manage each department → **Total participation for Department**
### Works_In
- An employee can work in **at most one department**
- A department can have **many employees**  
    → **1:N** relationship
- Each employee **must** work in a department → **Total participation for Employee**
- Each department **must have employees** → **Total participation for Department**
### Combined Summary
- Employee can manage at most one department.
- Employee must work in one department.
- Exactly one employee must manage a department.
- Each department must have employees.

---
## Weak Entities and Weak Relationships
 
Used when an entity **cannot exist without** another (its “owner”).  
If the owner is deleted, the weak entity is also removed.

**Notation:**
- **Double-lined rectangle** → Weak Entity
- **Double-lined diamond** → Weak Relationship
- **Dashed underline** → Weak key attribute

**Example:**
- A _Player_ has _Purchases_.
- Purchases exist only while the player exists.  
    → _Purchase_ is a weak entity; _Player_ is the owner.

**Key rule:**  
Primary Key = Owner’s PK + Weak Key of Subject  
e.g. (PID, Date) uniquely identifies a Purchase.

---
## Extended ER – ISA (“is a”) Hierarchies

Used for **subclass relationships**.

**Example:**

Employees
 ├── Hourly_Emps
 └── Contract_Emps

**Attributes:**
- `Employees`: name, ssn, lot
- `Hourly_Emps`: hourly_wages, hours_worked
- `Contract_Emps`: contractid

**Constraints:**
- **Overlap constraint:** Can someone belong to both subclasses?
- **Covering constraint:** Must every Employee belong to at least one subclass?

**Reasons for Using ISA:**
- Add attributes specific to a subclass
- Identify entities that participate in relationships differently
---
