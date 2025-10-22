---
date: 2025-10-21
noted: true
tags:
  - week3
---
```table-of-contents
```

> [!info] Resources
> [📊 PowerPoint](WK3.LC1.Functional_Dependencies_And_Normal_Forms.pdf)
> [📽️Lecture Recording]()

---
## The YouTube video linked below is *very* useful for this lecture/topic (Channel is useful for the whole module). 

[Normalisation](https://www.youtube.com/watch?v=GFQaEYEc8_8)
[Boyce-Codd Normal Form (BCNF)](https://www.youtube.com/watch?v=VWnKUKH4tLg)

---
## Functional Dependencies (FDs)
### Definition
A **Functional Dependency** exists when the value of one attribute (or set of attributes) determines another.  

If `A → B`, then attribute **B** is _functionally dependent_ on **A**.
### Example

![[Pasted image 20251022064818.png]]
`ID → NAME`  
This means each `ID` value determines one `NAME`.
### Why FDs Matter
If FDs are not managed properly, anomalies can occur:
- **Insertion anomaly:** Can’t insert data due to missing dependency.
- **Update anomaly:** Must update multiple tuples for consistency.
- **Deletion anomaly:** Deleting a row may remove useful data elsewhere.

To prevent these, we **decompose** the table based on FDs.

---
## Decomposition
Decomposition splits a relation into smaller ones to remove redundancy.
### Example
If `ID → NAME`, we can create:
1. Main table without `NAME`.
2. Separate table with `{ID, NAME}`.
![[Pasted image 20251022065213.png]]
- Reduces redundancy.
- Maintains consistency through FDs.

---
## Understanding Functional Dependencies

Example FDs:
- `CUSTOMNAMEVISIBLE` → key
- `ID` → `GLOWING`

If a dependency like `NAME → MOTION` doesn’t hold consistently, it violates FD rules.

---
## Analysing FDs and Finding Keys

Given a relation `R = {A, B, C, D, E, F, G}`  
and FDs:  `A → B`, `B → C`, `BC → D`, `D → EFG`

We can **find hidden dependencies** using the **closure of F**, denoted `F⁺`.

---
### Armstrong’s Axioms (FD Inference Rules)
Used to derive all implied dependencies.
1. **Reflexivity:** If Y ⊆ X, then X → Y
2. **Augmentation:** If X → Y, then XZ → YZ
3. **Transitivity:** If X → Y and Y → Z, then X → Z
4. **Union:** If X → Y and X → Z, then X → YZ
5. **Decomposition:** If X → YZ, then X → Y and X → Z

These axioms are _sound and complete_ — all valid FDs can be derived from them.
#### Example Using F⁺

From the previous FDs:
- `A → B` and `B → C` imply `A → C` (transitivity).
- `BC → D` and `D → EFG` imply `BC → DEFG`.
- `A → B, B → C, BC → DEFG` → `A → ABCDEFG`.  
    Thus, **A is a key** (can determine all attributes).

---
## Normalisation
### Purpose
Normalisation removes redundancy and minimises anomalies by organising attributes into well-structured tables. (Introduced by **E.F. Codd (1972)**).

A relation in a given **normal form** (1NF, 2NF, 3NF, BCNF) satisfies specific conditions that ensure data integrity.

---
## First Normal Form (1NF)

A relation is in **1NF** if:
- All attributes have **atomic (indivisible)** values.
- No repeating groups or sets of values.

![[Pasted image 20251022065947.png]]
### Example
If a table cell contains multiple names or lists, it violates 1NF.

---
## Candidate Keys & Attributes

- **Candidate Key:** Minimal set of attributes uniquely identifying a tuple.
- **Prime Attribute:** Part of a candidate key.
- **Non-prime Attribute:** Not part of any candidate key.

#### Example:  
For `R(Age, CustomName, Name, Custom)`  
Candidate keys: `{Age}` and `{CustomName, Name}`  
Prime attributes = `Age`, `CustomName`, `Name`  
Non-prime = `Custom`

---
## Second Normal Form (2NF)

A table is in **2NF** if:
- It’s already in **1NF**.
- Every **non-prime attribute** is **fully functionally dependent** on the entire primary key.

If a non-prime attribute depends on **part** of a composite key → it violates 2NF.

#### Example:  
Primary key = `(CustomName, Name)`  
If `Name → Custom`, then partial dependency exists → **not in 2NF**.  
If `(CustomName, Name) → Custom`, then fully dependent → **2NF satisfied**.

**To check for 2NF:**
1. Identify candidate key(s).
2. Check if any non-prime attribute depends on only part of the key.

If yes → **decompose** the relation.

---
## Example of 2NF Violation

![[Pasted image 20251022065715.png]]
Relation key = `{(Su, P)}`  
If `Su → L`, where `L` is a non-prime attribute → violates 2NF.

Decompose into:
- `(Su, P, St)`
- `(Su, L)`

---
## Third Normal Form (3NF)

![[Pasted image 20251022065817.png]]

A relation is in **3NF** if:
- It’s in **2NF**.
- For every FD `X → A`, one of the following is true:
    - The FD is **trivial** (`A ∈ X`).
    - **X** is a **superkey**.
    - **A** is a **prime attribute** (part of some key).

In simpler terms:  
**No non-prime attribute should determine another non-prime attribute.**
#### Example
If `M# → MTEL#`, both non-prime attributes, relation is **not in 3NF**.

Fix: Decompose into:
- `(M#, MTEL#)`
- `(E#, N, A, J#, M#)`
![[Pasted image 20251022065842.png]]

---
## Boyce-Codd Normal Form (BCNF)

BCNF is a **stronger** version of 3NF.

![[Pasted image 20251022070057.png]]

A relation is in **BCNF** if, for every FD `X → A`:
- The dependency is trivial (`A ∈ X`), or
- **X is a superkey**.

If a non-superkey determines another attribute → violates BCNF.

**BCNF eliminates all redundancy that can be inferred from FDs alone.**

---
## Steps for Normalisation

1. **Find all candidate keys** using FD closure (F⁺).
2. **Check the normalisation level** (1NF → 2NF → 3NF → BCNF).
3. **Decompose** if any dependency violates the desired normal form.

---
## Summary

- Normalisation **optimises tables** and prevents anomalies.
- **Functional dependencies** reveal how attributes are related.
- Use **Armstrong’s axioms** to derive implied dependencies.
- **1NF:** Atomic values only.
- **2NF:** Remove partial dependencies.
- **3NF:** Remove transitive dependencies.
- **BCNF:** Only key-based dependencies remain.
- Always verify keys using **F⁺ closure** and normalise as needed.

---
