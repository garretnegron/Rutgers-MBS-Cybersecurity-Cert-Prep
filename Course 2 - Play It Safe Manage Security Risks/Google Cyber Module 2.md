# Security Frameworks & Controls
## Frameworks
`Security Frameworks` are guidelines used for building plans to help mitigate risk and threats to data and privacy. Frameworks support organizations’ ability to adhere to compliance laws and regulations.

> **People are the biggest threat to security.**

These frameworks encompass both virtual and physical security, guiding organizations in maintaining safety across all aspects of their operations.

### Specific Frameworks and Controls
#### Cyber Threat Framework (CTF)
* Developed by the US government to provide a common language for describing and communicating information about cyber threat activity.
> Providing a common language to communicate info about threat activity.
#### International Organization for Standardization/International Electrotechnical Commision (ISO/IEC) 27001
* Internationally recognized and used framework.
* Framework outlines requirements for an information security management system, best practices, and controls that support an orgs ability to **manage risk**.
## Controls
`Security Controls` are safeguards designed to reduce specific security risks.<br>
Security controls are the measures organizations use to lower risk and threats to data and privacy.
* Three Common Types of Controls
    + **Encryption**
        - The process of converting data from a readable fromat to an encoded format.
        - (Typically involves converting plain text to cypher text.)
    + **Authetication**
        - Process of identifying who someone or something is.
        - EXAMPLE: Biometrics (Unique physical characteristics) can be used to verify a person's identity.
    + **Authorization**
        - Concept of granting access to specific resources within a system.

> [!WARNING]
> `Vishing` is the exploitation of electronic voice communication to obtain sensitive information or to impersonate a known source.

>[!NOTE]
Controls can be `physical`, `technical`, and `administrative` and are typically used to ***prevent***, ***detect*** or ***correct*** security issues.

Examples of **physical** controls:
* Gates, fences, and locks
* Security guards
* Closed-circuit television (CCTV), surveillance cameras, and motion detectors
* Access cards or badges to enter office spaces

Examples of **technical** controls:
* Firewalls
* MFA
* Antivirus software

Examples of **administrative** controls:
* Separation of duties
* Authorization
* Asset classification

## Module End Questions

1. How do security frameworks enable security professionals to help mitigate risk?<br>
***They are used to establish guidelines for building security plans.***
>[!TIP]
>Security frameworks are used to establish guidelines for building security plans that enable security professionals to help mitigate risk.

2. Competitor organizations are the biggest threat to a company’s security.<br>
***False***
>[!TIP]
>**People** are the biggest threat to a company’s security. This is why educating employees about security challenges is essential for minimizing the possibility of a breach.

3. Fill in the blank: Security controls are safeguards designed to reduce _____ security risks. <br>
***specific***
>[!TIP]
>Security controls are safeguards designed to reduce specific risks.
4. A security analyst works on a project designed to reduce the risk of vishing. They develop a plan to protect their organization from attackers who could exploit biometrics. Which type of security control does this scenario describe?<br>
***Authentication***
>[!TIP]
>This describes authentication, which is the process of implementing controls to verify who someone or something is before granting access to specific resources within a system.

# The CIA Triad: Confidentiality, Integrity, and Availability
>OUR JOB AS CYBER SECURITY ANALYSTS --> Help protect our organizations sensitive data from threat actors.

`CONFIDENTIALITY` - Only authorized users can access specific assets.

`INTEGRITY` - Data is correct authentic and reliable.

`AVAILABILITY` - Data is accesible to those who are authorized to access it.

Maintaining an acceptable level of risk and ensuring systems and policies are designed with these elements in mind helps establish a successful **security posture**.

# NIST Frameworks
`NIST CYBERSECURITY FRAMEWORK (CSF)`<br>
>A voluntary framework that consists of standards, guidelines, and best practices to manage cybersecurity risk.

The latest version, CSF v2.0, consists of **six** important core functions:
* Govern
* Identify
* Protect
* Detect
* Respond
* Recover

>[!NOTE]
> `NIST S.P 800-53` expands on the CSF by offering a unified framework for protecting the security of infromation systems within the federal government.

## The Six Functions of the NIST Cybersecurity Framework
### Govern
>Emphasizes the importance of strong cybersecurity governance across all levels of the organization.

It's about establishing and maintaining the structures and processes needed to effectively manage cybersecurity risk.

This includes:
* Setting clear cybersecurity objectives
* Ensuring leadership commitment
* Developing and implementing comprehensive risk management strategy
* Continuosly improving cybersecurity performance

### Identify
>The management of Cybersecurity risk and its effect on an organizations people and assets.

### Protect
>The strategy used to protect an organization through the implementation of policies, procedures, training, and tools that help mitigate cybersecurity threats.
### Detect
> Identifying potential security incidents and improving monitoring capabilities to increase the speed and efficiency of detections.
### Respond
> Making sure that the proper procedures are used to contain, neutralize, and analyze security incidents, and implement improvements to the security process.
### Recover
> The process of returning affected systems back to normal operation.

# OWASP Principles and Security Audits
## OWASP Security Principles
* `Minimize Attack Surface Area`
    + Disable software features
    + More complex password requirements
* `Principle of Least Privilege`
    + Users should have the least amount of access required to perform their everyday tasks
    + Philosophy is that if a threat actor steals an account they won't get access to everything
* `Defense in Depth`
    * An org should have multiple security controls that address risks and threats in different ways
    (MFA, Firewalls, etc)
* `Separation of Duties`
    + Critical actions should rely on multiple people
    + No one should be given so many privileges that they can abuse org systems
* `Keep Security Simple`
    + Unnecessary complexity should be avoided when developing security controls.
* `Fix Security Issues Correctly`
>[!NOTE]
> Attack surface area is all the potential vulnerabilities that a threat actor could exploit.

## Additional OWASP Security Principles
* `Establish Secure Defaults`
    + This principle means that the optimal security state of an application is also its default state for users; it should take extra work to make the application insecure. 
* `Fail Securely`
    + Fail securely means that when a control fails or stops, it should do so by defaulting to its most secure option. For example, when a firewall fails it should simply close all connections and block all new ones, rather than start accepting everything.
* `Don't Trust Services`
    + Many organizations work with third-party partners. These outside partners often have different security policies than the organization does. And the organization shouldn’t explicitly trust that their partners’ systems are secure. 
* `Avoid Security by Obscurity`
    + The security of an application should not rely on keeping the source code secret. Its security should rely upon many other factors, including reasonable password policies, defense in depth, business transaction limits, solid network architecture, and fraud and audit controls.

## Plan a Security Audit
>[!IMPORTANT]
> `Security Audit` is a review of an organization's security controls, policies, and procedures against a set of expectations.

There are 2 kinds:
* Internal Security Audit
    + Identify org risk
    + Assess controls
    + Correct compliance issues
* External Security Audit

### Common Elements of Internal Audits
* Establishing scope and goals
* Conducting risk assessment
* Completing a controls assessment
* Assessing compliance
* Communicating results to stakeholders




## Complete a Security Audit
### Audit Questions
What is the audit meant to achieve?

Which Assets are most at risk?

Are current controls sufficient to protect those assets?

What controls and compliance regulations need to be implemented?

### Controls Assessment
* `Administrative Controls`
    + Related to the human component of cybersecurity
    + Policies and procedures on how an org manages data
* `Technical Controls`
    + Hardware and software solutions used to protect assets
* `Physical Controls`
    + Surveilance cameras
    + Locks

### Compliance Assessment
Laws and stuff

### Stakeholder Communication
>[!TIP]
>When communicating the results of an internal audit to stakeholders, the communication should include a summary of the audit's scope and goals; a list of risks and compliance requirements that need to be addressed; and a recommendation about how to improve the organization’s security posture.

>[!CAUTION]
> Document needs to be reviewed for thoroughness. Some topics can use more notes and overall info.