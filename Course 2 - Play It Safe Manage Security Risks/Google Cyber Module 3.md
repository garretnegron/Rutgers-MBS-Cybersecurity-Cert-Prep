# Security Information and Event Management (SIEM) Dashboards
### Common Log sources:
* Firewall logs
* Network logs
* Server logs

>[!NOTE]
> `Security Orchestration, Automation, and Response (SOAR)` - Research

Collection of applications, tools, and workflows that uses automation to respond to security events.<br>(Essentially, this means handling common-security related issues with use of SIEM tools is expected to become a more streamlined process; less manual intervention!)

## Types of SIEM Tools
* Self-hosted
* Cloud-hosted

### SPLUNK Enterprise / SPLUNK Cloud
Both allow you to review an organization's data on dashboards. Splunk has it's own query language, Splunk Processing Language (`SPL`).

#### Splunk Dashboards and their purposes:
##### Security Posture Dashboard
Designed for Security Operarions Centers (SOCs). Displays the last 24hr of an org's notable security-related events and trends. It allows security professionals to determine if security infrastructure and policies are performing as designed.

##### Executive Summary Dashboard
Analyzes and monitors the overall health of the org over time. This helps security teams improve security measures that reduce risk.

##### Incident Review Dashboard
Allows analysts to identify suspicious patterns that can occur in the event of an incident. It assists by highlighting **higher risk items** that need immediate review by an analyst.

##### Risk Analysis Dashboard
Helps analysts identify risk for each risk object (e.g., a specific user, a computer, or an IP). It shows changes in risk-related activity, such as a user logging in outside of normal working hours or unusuallyu high network traffic from a user.


### Chronicle
Cloud native SIEM tool from `Google` that retains, analyzes, and searches log data to ID potential security threats, risks, and vulnerabilities.

Analysts can collect:
- A specific asset
- A domain name
- A user
- An IP Address

#### Chronicle Dashboards and their purpose:
##### Enterprise Insights Dashboards
Highlights recent alerts. IDs suspicious domain names in logs, known as indicators of compromise (IOCs). Results labeled with *confidence score* to indicate the likelihood of a threat. Also indicates *severity level* that indicates significance of each threat to org.

##### Data Ingestion and Health Dashboard
Shows the number of event logs, log sources, and success rates of data being processed into Chronicle.

##### IOC Matches Dashboard
Indicates the top threats, risks, and vulnerabilities to the organization.

##### Main Dashboard
High level summary of info.

##### Rule Detections Dashboard
Displays statistics related to incidents with the highest occurrences, severities, and detections over time.

##### User Sign-in Overview
Provides information about user access behavior across the organization. 
<br>
<br>
>[!IMPORTANT]
> These tools allow analysts to reduce risk by identifying, analyzing, and remediating the highest priority items in a timely manner.
> 