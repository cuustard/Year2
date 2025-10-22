---
date: 2025-10-22
noted: false
tags:
  - week3
---
```table-of-contents
```

> [!info] Resources
> [📊 PowerPoint](WK3.LC1.Software_Architecture.pdf)
> [📽️Lecture Recording]()


---

The software architecture of a system is a set of structures needed to reason about the system, which comprise software elements, relations amongst and properties of both. In laymen's terms:

> [!info] Definition 
> Software architecture defines the key structures of a system, showing its software elements, their relationships, and their properties - providing the basis for reasoning about the system’s behaviour and design. #keyTermDefinition

> Architecture is a set of **structures**..."

- A **structure** is a set of elements held together by relations
- Architecture consists of structures, and structures consist of elements and relations
- Architecture purposely omits certain information that is not useful for reasoning about the system

Software elements can and may be software sub-systems of components _(relations indicated by links between elements)_:

![[Pasted image 20251022022542.png]]

---
## The Software Design Process

![[Pasted image 20251022023256.png]]

The design process may involve developing several models of the system at different levels of abstractions:
- **Architectural Design**: The sub systems making up the system and their relationships are identified and documented. Model of control is identified.
- **Interface Design**: For each sub-system, it's interface with other sub-systems is designed and documented.
- **Component Design**: Services (i.e. [[WK1.LC1.Software_Requirements#Types of Requirements And Metrics for Measuring|functional requirements]]) are allocated to different components and the interfaces of these components are designed.
- **Data Structure Design**: The data structures used in the system implementation are design in detail.
- **Algorithm Design**: The algorithms used to provide services are designed in detail and specified.

---
## The Steps in Architectural Design

These activities are common to all architectural design processes:
- **System Structuring**: The system is structured into a number of principal sub-systems or components and the communication between sub-systems is identified.
- **Control Modelling**: A general model of control relationships between the parts of the system is established.
- **Modular Decomposition**: Each sub-system is decomposed into modules.

---
## Describing Architecture

Formal Notations:
![[Pasted image 20251022025027.png]]

Architecture Description Languages:
![[Pasted image 20251022025055.png]]

Semi-Formal:
![[Pasted image 20251022025131.png]]

Box and Line Notation:
![[Pasted image 20251022025152.png]]
![[Pasted image 20251022025546.png]]

At its most abstract level, an architectural design may be depicted as a block diagram (using the above box and line notation). 
- It comprises the system's major sub-systems, their components, and relations
- Sub-systems are often identified by clustering logical functionality
- Boxes within boxes indicates that the sub-system itself has been decomposed to components (we usually keep decomposition to two levels)
- Links represent function calls, data, or control signals that are passed from component to components in the direction of the arrow

---
## Identifying Sub-Systems and Their Interfaces

1. Identify **major** functions the system is required to provide.
	1. These can be distilled from textual [[WK1.LC1.Software_Requirements|requirements]] requirements and [[WK2.LC1.Use_Cases|use cases]].
2. Associate the major systems functions with sub-systems by grouping together logically similar functions.
	1. E.g. functions concerned with specific system tasks, performance-critical functions or security-critical functions etc.
3. Sub-systems may be decomposed further using the same principle.
	1. Limit the system decomposition to two levels
4. Specify sub-system interfaces.

E.g.:

![[Pasted image 20251022030345.png]]
![[Pasted image 20251022030356.png]]
![[Pasted image 20251022030405.png]]
![[Pasted image 20251022030413.png]]

---
### Example: An Alarm System

Consider an intruder alarm system that activates a siren and notifies the local control centre when its sensors are tripped. The alarm system has:
- Movement (motion), door and window sensors
- A video system that is activated when potential intruders are detected. The date, time, property address, and video of potential intruders is relayed to an external control centre.
- A messaging system that sends a text message together with a preconfigured number of still images of potential intruders to the home owner.

Task: Identify possible sub-systems for the alarm system and their interaction. Hint: Group together related functionality to form sub-systems. 

#### Identifying Sub-Systems

1. Read through the system description to establish what the system is required to do OR what the system does. (See above list.)
2. List the system functions. (Sensing intruders, Activating siren, Notifying local control, activating video, Messaging home owner)
3. Group related functionality. (Sensor, Siren, Video relay, video, message)
4. Associate functionality of sub-systems
5. For each sub-system establish if there is need to partition further

Link sub-systems that interact with each other (i.e. those that exchange data or control information). Point your arrow in the direction of the data or control flow:
![[Pasted image 20251022031310.png]]
![[Pasted image 20251022031325.png]]

Label calls & control flows:
![[Pasted image 20251022031345.png]]

#### Specifying Sub-System Interfaces

The description of a sub-system or component interface should include the following elements:
- **Interface Name**: A unique ID for the interface `e.g. ISensor`
- **Operations**: The name of each operation, together with input parameters and output/return, e.g. `motionDetected(:int)`
	- Operation Name: motionDetected
	- Input: None
	- Output/return: int (indicating location of sensor or sensor number)
- **Exceptions**: The name and data context for operation exceptions (i.e. what causes the exception, e.g. invalid input parameter)
- **Service Quality** (optional): Non-functional properties associated with the service provided at the interface.

An interface may have several operations, each with its own input and output parameters. An output parameter represents what is returned by an operation. For example, the `ISensor` (`I` naming convention means Interface) interface may have the following operations:
- `motionDetected(): int`
- `windowOpened(): bool`
- `doorOpened(): bool`

##### Ball and Socket

![[Pasted image 20251022032448.png]]


##### Guidelines for Interfaces

![[Pasted image 20251022032645.png]]

Service provider implements all the operations defined in its interface, e.g.
![[Pasted image 20251022032614.png]]

Service user calls operations provided by the interface, e.g.
![[Pasted image 20251022032636.png]]

#### Alarm System with Interfaces (Ball and Socket)
![[Pasted image 20251022032733.png]]

##### Interface Operations and Parameters

![[Pasted image 20251022032853.png]]

