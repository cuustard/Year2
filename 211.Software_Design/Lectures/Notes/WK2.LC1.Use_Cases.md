#week2

> [!info] Resources
> [📊 PowerPoint](WK2.LC1.Use_Cases.pdf)
> [📽️Lecture Recording]()

```table-of-contents

```
---
## Use Cases Overview

Behavioural model of a system describing **how the system responds to external stimuli**.
- Useful because:
    - Describe scenarios understandable by stakeholders
    - Textual → easy to communicate
    - Can be used to **derive test cases**
    - Part of **UML (Unified Modelling Language)**
#### Components
- **Use Case Diagram**: High-level overview of system actors and interactions
- **Use Case Description**: Detailed scenarios (textual)

**Key terms**:
- **Actor**: User, system, or device interacting with the system
- **Use case**: High-level goal (verb-noun phrase) that an actor wants to achieve
- **Primary actor**: Main user achieving the goal
- **Secondary actor**: Helps the system achieve the primary actor’s goal

---
##  Modelling

Models simplify reality: **deal with complexity, abstraction, separation of concerns**
- UML models:
    - Static: Class, object, component
    - Dynamic: State charts, activity diagrams, sequence diagrams
- Benefits: 
	- Focus on specific concerns, perform consistency checking

---
## Use Case Descriptions

- **Template structure**:

```
Use Case Name: <Name>
Scope: <System>
Primary Actor: <Actor>
Secondary Actors: <Actors>
Preconditions: <Conditions to start>
Flow of Events: <Step-by-step interactions>
    - Primary scenario ("happy day")
    - Alternate/secondary scenarios
Postconditions: <System state at end>
Non-functional requirements: <Optional annotations>
```
**Example: Submit Coursework**

- Primary scenario: Student submits coursework → Teaching Office records → Tutor marks → Lecturer returns → Teaching Office updates system → Student receives mark

- Secondary scenario: Late submission → marked as late, notified to lecturer
---
## Use Cases → Requirements

Use cases help **derive functional requirements.**

Example derived requirements:
```
CMS1.1 A student shall be able to submit coursework once issued.
CMS1.2 System shall record assignment, student name, date/time.
CMS1.3 On deadline expiry, system reports submissions to lecturer/office.
CMS1.4 Late submissions are flagged with date and notified.
CMS1.5 Lecturer can access submissions post-issue.
```
Each requirement is **uniquely identified** for management

---
## Include vs Extend

**include**: Extracts **common mandatory behaviour** across multiple use cases
**extend**: Adds **optional or conditional behaviour** to a use case

**Arrow directions matter** in UML

**Example: Facebook**
```
Primary Actor: Facebook User
Use Cases: Create Account, Upload Photo, Add Friend, Accept Terms
<<include>> Edit Privacy Settings
<<extend>> Accept Terms
```

---
## Use Case Levels (Granularity)

|Level|Description|Example|
|---|---|---|
|Cloud|Very high-level / business goal|Maximize users|
|Sea|User goal|Add Friend, Create Account|
|Fish|Sub-goal / reusable fragment|Login, Accept Terms|
|Bottom-of-ocean|Too detailed / low-level|Enter Password|

---
## Use Case Testing

- Create at least **one test case per flow**
- Identify variables & significant options
- Combine into test cases → assign values
---
## Example: ATM System

- **Actors**: Bank Customer (primary), Bank Database (secondary)
- **Use Cases**:
    - Withdraw cash
    - Display balance
    - Display last 10 transactions
    - **Verify customer** (include in all use cases)

**Notes**: All ATM services require verified customers.

---
## Use Case Diagram Management

- Use sub-systems to manage complexity
- Avoid:
    - Excessive structuring
    - Functional decomposition
- Apply **include/extend** only when necessary

---