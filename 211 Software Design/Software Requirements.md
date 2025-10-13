noted: 08/10/2025 #week1 

> [!info] Resources
> [📊 PowerPoint](Resources/SoftwareRequirements.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=701d3f86-17ee-4bfd-a3d9-b36300370351&start=0)

> [!info] Required Reading
> [📘 Software Engineering (10th Ed.), Ian Sommerville](GlobalEditionSoftwareEngineering10thEdition2016_IanSommerville.pdf)
> [📘 Integrated Requirements Engineering: A Tutorial, by Ian Sommerville](Resources/IntegratedRequirementsEngineeringATutorial2005_IanSommerville.pdf)

```table-of-contents

```

---

## What Software Requirements Are

A software requirement defines what the system under development should do (but not how it does it), and constraints under which it must do it.

> A **requirement**, according to the IEEE Standard Glossary of Software Engineering Terminology, is a _documented condition or capability_ that a user needs to solve a problem or achieve an objective, or that a software system or its components must meet to satisfy a contract, standard, specification, or other formally imposed document.

Software Requirements define the software's purpose and scope of the project. They serve as a contract between the development team and the customer. They are fundamental to the verification and validation of the system. It enables engineers to create test cases that cover all aspects the software they are developing. They guide the development process and act as a roadmap for the development team, ensuring the software meets it's intended purpose. Fixing requirements related errors at the implementation stage costs 10x more than at requirements.

## Writing Software Requirements

Guidelines for writing requirements:

- Use **Shall** for mandatory requirements
- Use **Should** for desirable requirements
- Highlight certain text to identify key parts
- Never assume the readers knowledge
- Involve many stakeholders
- Explain why each requirement is necessary

Requirements can be written at different levels of abstraction/detail for different stakeholders. For example, customers do not need as high of level of detail compared to the technical or development team so it's important requirements are written in a way that customers understand (in layman's terms). User requirements, intended for the customer, should be written using natural language, tables, and diagrams. For example:

- User Requirements:
	1. The patient management system shall generate monthly management reports showing the cost of drugs prescribed by each clinic during that month.
- System Requirements:
	1. On the last working day of each month, a summary of the drugs prescribed, their cost, and the prescribing clinics **shall** be generated.
	2. The system **shall** automatically generate the report for printing after **17:30** on the last working day of the month.

## Types of Requirements And Metrics for Measuring

There are two types of software requirements. Functional Requirements (FR) and Non-functional Requirements (NFR). FRs are for services that a system should deliver. NFRs specify the quality with which a system delivers its services. NFRs are **shall** statements that precisely specify these constraints.

A requirement document is usually a text document and includes a purpose, scope of the product, and a set of **shall** statements prescribing what the system will do (both FR and NFR). 

Metrics for specifying Non-functional requirements:

| Property            | Measure                                                                                                            |
| :------------------ | ------------------------------------------------------------------------------------------------------------------ |
| Speed (Performance) | Processed transactions/second<br>User/event response time<br>Screen refresh time                                   |
| Size                | Mbytes<br>No of ROM chips                                                                                          |
| Ease of Use         | Training time<br>Number of help frames                                                                             |
| Reliability         | Mean time to failure (MTTF)<br>Probability of unavailability<br>Rate of failure occurrence                         |
| Robustness          | Time to restart after failure<br>Percentage of events causing failure<br>Probability of data corruption on failure |
| Portability         | Number of target systems                                                                                           |

Requirements must be testable. To create tests for requirements, they must be defined specifically. 

## Requirements Engineering

Requirements Engineering is a systematic process of understanding the problem, specifying the solution, (and once the solution is validated) managing the requirements.

To understand the problem it is important to understand the context of said problem that the system is intended to address:
- What is the business goal?
- Who is the system for and other stakeholders?
- What is the operational environment?
- "Green field" or evolution of existing system?
- What can we change, what must we keep?

We can specify the proposed system by addressing the following questions:
- What is needed to achieve the business goal?
- What is needed to support the users?
- How do these requirements interact? (some may conflict and some will be higher priority than others)
- Are the requirements you have formulated the right requirements?

You must identify the important stakeholders in a system to discover their requirements. A system stakeholder is any person or organisation who is affected by the system and has a legitimate interest. They could include:
- End user
- Managers and others involved in the organisational processes influenced by the system
- Engineers responsible for the development and maintenance
- People responsible for systems that will interface with the system under development
- External bodies such as regulators or certification authorities
