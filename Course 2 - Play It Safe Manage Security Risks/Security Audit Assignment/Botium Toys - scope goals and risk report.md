# Botium Toys: Scope, Goals, and Risk Assessment Report

## Scope and Goals of the Audit

### Scope

The scope is defined as the entire security program at Botium Toys. This means all assets need to be assessed alongside internal processes and procedures related to the implementation of controls and compliance best practices.

### Goals

Assess existing assets and complete the controls and compliance checklist to determine which controls and compliance best practices need to be implemented to improve Botium Toys' security posture.

---

## Current Assets

Assets managed by the IT Department include:

- On-premises equipment for in-office business needs
- Employee equipment:
  - Desktops and laptops
  - Smartphones
  - Remote workstations
  - Headsets
  - Cables
  - Keyboards
  - Mice
  - Docking stations
  - Surveillance cameras
- Storefront products available for retail sale on-site and online, stored in the company's adjoining warehouse
- Management of systems, software, and services:
  - Accounting
  - Telecommunications
  - Databases
  - Security systems
  - E-commerce platforms
  - Inventory management systems
- Internet access
- Internal network
- Data retention and storage
- Legacy system maintenance, including end-of-life systems requiring human monitoring

---

## Risk Assessment

### Risk Description

Currently, there is inadequate management of assets. Additionally, Botium Toys does not have all of the proper controls in place and may not be fully compliant with U.S. and international regulations and standards.

### Control Best Practices

The first of the five functions of the NIST Cybersecurity Framework (CSF) is **Identify**. Botium Toys will need to dedicate resources to identify assets so they can appropriately manage them.

Additionally, the company should:

- Classify existing assets
- Determine the impact of asset loss
- Evaluate the effect of system failures on business continuity

### Risk Score

**Risk Score: 8/10**

This score is considered fairly high due to a lack of controls and insufficient adherence to compliance best practices.

### Additional Comments

The potential impact from the loss of an asset is rated as **Medium** because the IT department does not know which assets would be at risk.

The overall risk of asset compromise or regulatory fines is considered **High** because Botium Toys lacks necessary controls and does not fully adhere to compliance requirements designed to protect sensitive data.

#### Current Findings

##### Access Control

- All employees currently have access to internally stored data.
- Employees may also be able to access cardholder data and customer PII/SPII.
- Least privilege has not been implemented.
- Separation of duties has not been implemented.

##### Data Protection

- Encryption is not used to protect customer credit card information.
- Customer payment data is accepted, processed, transmitted, and stored locally in the internal database.

##### Availability and Integrity

- Controls are in place to support data integrity.
- Availability controls have been implemented by the IT department.

##### Network Security

- A firewall is deployed and configured with appropriate security rules.
- Antivirus software is installed and regularly monitored.
- No Intrusion Detection System (IDS) has been implemented.

##### Business Continuity

- No disaster recovery plan exists.
- No backups of critical data are maintained.

##### Privacy and Compliance

- A process exists to notify EU customers within 72 hours of a security breach.
- Privacy policies, procedures, and processes have been developed and enforced.

##### Password Management

- A password policy exists but does not meet modern complexity requirements.
- Requirements are not centrally enforced.
- No centralized password management system is in place.
- Password recovery and reset requests can negatively impact productivity.

##### Legacy Systems

- Legacy systems are monitored and maintained.
- No regular maintenance schedule exists.
- Intervention procedures are not clearly defined.

##### Physical Security

The facility includes:

- Sufficient locking mechanisms
- Up-to-date CCTV surveillance
- Functioning fire detection systems
- Functioning fire prevention systems

These controls protect the main office, storefront, and warehouse facilities.