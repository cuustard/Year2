> [!info] Resources
> [⚒️ Workshop Task](211.Software_Design/Workshops/Slides/WK1.WKSP1.Software_Requirements.pdf)
> [📽️Lecture Recording]([https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=649f371b-8e90-46ed-b7e8-b36600e31e4c&start=0](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=649f371b-8e90-46ed-b7e8-b36600e31e4c&start=0))

> [!info] Info
> This lecture went over what we have to do for the [[WK1.LC2.Software_Requirements_Solution 1|Workshop]]. Visit that note to see our answers.

```table-of-contents
```
---
## Software Requirements Recap

There are two types of [[WK1.LC1.Software_Requirements]]. Functional Requirements (FR) and Non-Functional Requirements (NFR). FR specifies the services that a system should deliver. NFR specifies the quality with which a system delivers its services. For example:
- **FR**: The ATM **shall** enable users to withdraw cash
- **NFR**:
	- Cash withdrawal service **shall** be available for at least 23hours a day
	- The ATM system **shall** be delivered in no more than 5 months
	- All customer data shall be stored in an encrypted form to protect against unauthorised access or processing

When writing Software Requirements, use language in a consistent way. Use **shall** for mandatory requirements, and **should** for desirable/useful requirements. For example:
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

---
## Task 1: Mary's Smart Home

### The Problem

Mary is 65 years old and lives alone. She has several health problems including high blood pressure and high cholesterol levels. Mary gets a smart fridge to help her manage her health.

- The fridge is able to read, store, and communicate RFID information on food packages.
- The fridge communicates with a smart home control system in the home. It detects the presence of spoiled food and receives a diet plan from Mary’s dietician. The fridge uses Mary’s diet plan to monitor what food items she is consuming and sends a weekly report to her GP (doctor).
- An important part of Mary's diet is to ensure minimum liquid intake. The fridge monitors Mary’s liquid consumption and notifies the emergency services when the liquid intake falls consistently below a minimum threshold.
- Mary is concerned about her health, but worried about her personal details falling into wrong hands

Stakeholders interested in the development and smooth running of healthcare smart home system (SHS):
- **Age Concern representative (AC)**: represents Mary and others like her. AC must best represent Mary’s desires and concerns.
- **Government Health Committee member (GHC)**: a government representative well versed in NHS procedures and policies whose chief role is to ensure that NHS practices are being abided by.
- **System Developer (SD)**: a system developer who knows about smart home technologies and how much they cost etc. SD’s role is to suggest possible technologies and keep the team grounded in reality.

### The Task

1. For each stakeholder, write down 2 possible requirements for the SHS, in the form of **shall** statements.
	- Each set of requirements should be written from the perspective of the chosen stakeholder.
	- Your requirements should (a) avoid including design details; (b) avoid vague requirements such as “the system should be secure” or “the system should be user-friendly”.
	- For each requirement identified above, state whether it is a functional or non-functional requirement.
2. Identify any potential conflicts between requirements from different stakeholders. Suggest how you might resolve these conflicts.
3. Write down your final list of non-conflicting SHALL statements (revised requirements).

### Our Answers

Thoughts and requirements for each stakeholder:

| Stakeholder | Thoughts                                                                        | Requirement                                                                                                                                                                     | Clashes                                                                                                                      |
| ----------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| AC          | Mary has concerns about personal details available to unauthorised individuals. | Patients personal data **shall** be encrypted when stored and transmitted through end to end encryption in order to minimise unauthorised data access. (**Non Functional**)<br> | This may conflict with GHC over data transmission concerns.<br><br>This may conflict with AC due to data transmission costs. |
| AC          | Mary would like the smart fridge to monitor health concerns.                    | The smart fridge **shall** actively monitor the data required in order to meet Mary's expectations. (**Functional**)                                                            |                                                                                                                              |
| GHC         |                                                                                 | A weekly report **shall** be sent to Mary's GP following the NHS practice and procedure. (**Functional**)                                                                       | This may conflict with AC due to concerns regarding data transmission.                                                       |
| GHC         |                                                                                 | Guidelines and requirements **shall** be followed in line with NHS practices and procedures. (**Functional**).                                                                  |                                                                                                                              |
| SD          |                                                                                 | he home technologies used **shall** be kept within Mary's budget costs. (**Non-Functional**)                                                                                    | This may conflict with AC due to concerns regarding data transmission as encryption and storage may incur higher costs.      |
| SD          |                                                                                 | The smart technology **shall** always be actively monitoring and in the event of downtime, an alert shall be made to both Mary and the registered GP. (**Functional**)          |                                                                                                                              |


Final Requirements rectifying clashes:
1. Patients’ personal data **shall** be encrypted when stored and transmitted using end-to-end encryption with cost-effective methods to minimise unauthorised access and comply with stakeholder requirements.
2. A completed consent form **shall** be required from Mary to allow data exchange between Mary and her GP.
3. The smart fridge **shall** actively monitor the data required to address Mary’s health concerns.
4. A weekly report shall be sent to Mary’s GP following NHS practices and procedures if Mary has completed the **consent** form.
5. All system guidelines and requirements **shall** comply with NHS practices and procedures.
6. The home technologies used **shall** remain within Mary’s budget, and for higher-priced technologies such as encryption, cost-effective methods shall be implemented to meet stakeholder requirements.
7. The smart technology **shall** always be actively monitoring, and in the event of downtime, an alert shall be sent to both Mary and her registered GP.

---
## Task 2: Mentcare

### The Problem
A patient information system to support mental health care is a medical information system that maintains information about patients suffering from mental health problems and the treatments that they have received.

Most mental health patients do not require dedicated hospital treatment but need to attend specialist clinics regularly where they can meet a doctor who has detailed knowledge of their problems.

To make it easier for patients to attend, these clinics are not just run in hospitals. They may also be held in local medical practices or community centres.

![[Excalidraw/Drawing 2025-10-16 12.33.24.excalidraw]]

Mentcare is an information system that is intended for use in clinics.

It makes use of a centralized database of patient information but has also been designed to run on Personal Computers (PCs), so that it may be accessed and used from sites that do not have secure network connectivity.

When the local systems have secure network access, they use patient information in the database but they can download and use local copies of patient records when they are disconnected.
### The Task

1. Write down three possible stakeholders for the Mentcare system.
2. Write down two Functional Requirements (FR) and two Non-Functional Requirements (NFR) for the Mentcare system.

### Our Answers

Stakeholders:
- Government Health Committee Member (GHC)
- System Developer (SD)
- Mental Patient Representative (MP)

FR:
1. The system **shall** allow authorized doctors and patients to securely access relevant medical data.
2. Doctors **shall** be allowed to download and use local copies of patient records when they are disconnected from the network.

NFR:
1. The patient record database **shall** be accessible 24/7
2. All patient records **shall** be stored in an encrypted form to protect against unauthorised access or processing.

---

## PlantUML