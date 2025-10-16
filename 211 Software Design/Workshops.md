> [!info] Resources
> [⚒️ Workshop Task](Resources/SoftwareRequirementsWorkshop1.pdf)

#doitlater 

```table-of-contents
```
## Recap

Functional Requirements (FR) and Non-Functional Requirements (NFR). FR specifies the services that a system should deliver. NFR specifies the quality with which a system delivers its services. For example:
- **FR**: The ATM **shall** enable users to withdraw cash
- **NFR**:
	- Cash withdrawal service **shall** be available for at least 23hours a day
	- The ATM system **shall** be delivered in no more than 5 months
	- All customer data shall be stored in an encrypted form to protect against unauthorised access or processing

Guidelines for writing requirements. Use language in a consistent way. Use **shall** for mandatory requirements, and **should** for desirable/useful requirements. For example, an app for buying train tickets:
- The app **shall** enable the user to buy train tickets
- The app **shall** support accessibility in accordance with the 2018 accessibility regulation
- The app **should** allow users to share their experience of using it

Also use text highlighting to identify key parts of the requirement. Don't make assumptions about the reader's knowledge. Involve as many stakeholders as possible. Include a rational explanation of why a requirement is necessary.

Speaking of stakeholders, you need to identify the important stakeholders in a system to discover their requirements. A **System Stakeholder** is any person or organisation who is affected by the system in some way and so has a legitimate interest. They could include:
- End users of the system
- Managers and others involved in the organisational processes influenced by the system
- Engineers responsible for the development and maintenance
- People responsible for systems that will interface with the system under development
- External bodies such as regulators or certification authorities 

## Task 1: Mary's Smart Home

### The Problem

Mary is 65 years old and lives alone. She has several health problems including high blood pressure and high cholesterol levels. Mary gets a smart fridge to help her manage her health.

- The fridge is able to read, store, and communicate RFID (Radio Frequency Identification) information on food packages.
- The fridge communicates with a smart home control system in the home. In particular, it detects the presence of spoiled food and receives a diet plan from Mary’s dietician. The fridge uses Mary’s diet plan to monitor what food items she is consuming and sends a weekly report to her GP (doctor).
- An important part of Mary's diet is to ensure minimum liquid intake. The intelligent fridge monitors Mary’s liquid consumption and notifies the emergency services in case the liquid intake falls consistently below a minimum threshold.
- Mary is concerned about her health, but worried about her personal details falling into wrong hands

There are a number of stakeholders interested in the development and smooth running of healthcare smart home system (SHS):
- **Age Concern representative (AC)** who represents Mary and others like her. AC must best represent Mary’s desires and concerns.
- **Government Health Committee member (GHC)**: a government representative well versed in NHS procedures and policies whose chief role is to ensure that NHS practices are being abided by.
- **System Developer (SD)**: a system developer who knows about smart home technologies and how much they cost etc. SD’s role is to suggest possible technologies and keep the team grounded in reality.

### The Questions

1. For each stakeholder, write down 2 possible requirements for the SHS, in the form of **shall** statements.
	- Each set of requirements should be written from the perspective of the chosen stakeholder.
	- Your requirements should (a) avoid including design details; (b) avoid vague requirements such as “the system should be secure” or “the system should be user-friendly”.
	- For each requirement identified above, state whether it is a functional or non-functional requirement.
2. Identify any potential conflicts between requirements from different stakeholders. Suggest how you might resolve these conflicts.
3. Write down your final list of non-conflicting SHALL statements (revised requirements).


## Task 2: Mentcare (A Patient Information System for Mental Health)

### The Problem

- A patient information system to support mental health care is a medical information system that maintains information about patients suffering from mental health problems and the treatments that they have received.
- Most mental health patients do not require dedicated hospital treatment but need to attend specialist clinics regularly where they can meet a doctor who has detailed knowledge of their problems.
- To make it easier for patients to attend, these clinics are not just run in hospitals. They may also be held in local medical practices or community centres.

![[Excalidraw/Drawing 2025-10-16 12.33.24.excalidraw]]

- Mentcare is an information system that is intended for use in clinics.
- It makes use of a centralized database of patient information but has also been designed to run on Personal Computers (PCs), so that it may be accessed and used from sites that do not have secure network connectivity.
- When the local systems have secure network access, they use patient information in the database but they can download and use local copies of patient records when they are disconnected.
### The Questions

1. Write down three possible stakeholders for the Mentcare system.
2. Write down at least two functional and two non-functional requirements for the Mentcare system
