
```table-of-contents
```

1. For each stakeholder, write down 2 possible requirements for the SHS, in the form of **shall** statements.
	- Each set of requirements should be written from the perspective of the chosen stakeholder.
	- Your requirements should (a) avoid including design details; (b) avoid vague requirements such as “the system should be secure” or “the system should be user-friendly”.
	- For each requirement identified above, state whether it is a functional or non-functional requirement.
2. Identify any potential conflicts between requirements from different stakeholders. Suggest how you might resolve these conflicts.
3. Write down your final list of non-conflicting SHALL statements (revised requirements).
---
### Problem 1 - Mary's Smart Home
---
**Age Concern representative (AC)**
- Mary has concerns about personal details available to unauthorised individuals. Therefore, patients personal data shall be encrypted when stored and transmitted through end to end encryption in order to minimise unauthorised data access. (Non Functional) 
  ***This may conflict with GHC due to concerns regarding data transmission, to rectify this a consent form shall be required in order to follow both stakeholders requirements.***
  ***This may conflict with AC due to concerns regarding data transmission as encryption and storage may incur higher costs. To meet both stakeholders requirements, prioritise cost effective encryption methods.***
- Mary would like the smart fridge to monitor health concerns. Therefore, the smart fridge shall actively monitor the data required in order to meet Mary's expectations. (Functional)

**Government Health Committee member (GHC)**
- A weekly report shall be sent to Mary's GP following the NHS practice and procedure. (Functional) 
  ***This may conflict with AC due to concerns regarding data transmission, to rectify this a consent form shall be required in order to follow both stakeholders requirements.***
- Guidelines and requirements shall be followed in line with NHS practices and procedures. (Functional).

**System Developer (SD)**
- The home technologies used shall be kept within Mary's budget costs. (Non Functional)
  ***This may conflict with AC due to concerns regarding data transmission as encryption and storage may incur higher costs. To meet both stakeholders requirements, prioritise cost effective encryption methods.***
- The smart technology shall always be actively monitoring and in the event of downtime, an alert shall be made to both Mary and the registered GP. (Functional)
---
**Age Concern representative (AC)**

- Mary has concerns about personal details available to unauthorised individuals. Therefore, patients personal data shall be encrypted when stored and transmitted through end to end encryption with cost effective methods in order to minimise unauthorised data access and comply with other stakeholders requirements. Additionally, a completed consent form shall be required from Mary to allow data exchange between Mary and her GP. (Non Functional) 
- Mary would like the smart fridge to monitor health concerns. Therefore, the smart fridge shall actively monitor the data required in order to meet Mary's expectations. (Functional)

**Government Health Committee member (GHC)**
- A weekly report shall be sent to Mary's GP following the NHS practice and procedure if Mary has completed the consent form. (Functional) 
- Guidelines and requirements shall be followed in line with NHS practices and procedures. (Functional).

**System Developer (SD)**
- The home technologies used shall be kept within Mary's budget costs. For higher priced technologies such as encryption, cost effective methods shall be implemented to comply with other stakeholder requirements. (Non Functional)
- The smart technology shall always be actively monitoring and in the event of downtime, an alert shall be made to both Mary and the registered GP. (Functional)
---

### Problem 2

Stakeholders:
- Government Health Committee Member (GHC)
- System Developer (SD)
- Mental Patient Representative (MP)

Functional Requirements (FR):
1. The system **shall** allow authorized doctors and patients to securely access relevant medical data.
2. Doctors **shall** be allowed to download and use local copies of patient records when they are disconnected from the network.

Non-Functional Requirements (NFR):
1. The patient record database **shall** be accessible 24/7
2. All patient records **shall** be stored in an encrypted form to protect against unauthorised access or processing.