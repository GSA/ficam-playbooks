---
layout: page
collections: playbooks
navtitle: Digital Worker Identity Playbook 
title: Digital Worker Identity Playbook 
pubdate: 2021-01
date: October 14, 2021
type: Markdown
permalink: /playbooks/dw/ 
description: The Digital Worker Identity Playbook is a practical guide for managing digital worker identities.
sticky_sidenav: true
sidenav: dw

subnav:
  - text: Executive Summary
    href: '#executive-summary'
  - text: A Three-Step Process for Digital Worker Identity Management
    href: '#a-three-step-process-for-digital-worker-identity-management'
  - text: Step 1. Determine the Impact
    href: '#step-1-determine-the-impact'
  - text: Step 2. Create an Identity
    href: '#step-2-create-an-identity'
  - text: Step 3. Provision an Identity
    href: '#step-3-provision-an-identity'
  - text: Conclusion
    href: '#conclusion'
  - text: References
    href: '#appendix-a-digital-worker-impact-evaluation-factors'
    
---

Version 1.1  
January 5, 2021

<a href="../../assets/img/logo-gsa.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-gsa.png" width="64" height='64' align="left" alt="U.S. General Services Administration Logo"></a>
<a href="../../assets/img/logo-cio.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-cio.png" width="64" height='64' align="left" alt="U.S. Federal Chief Information Officer Council Logo"></a><br><br><br>

This playbook is a collaboration between the Identity, Credential, and Access Management Subcommittee of the Federal Chief Information Security Officer (CISO) Council and the General Services Administration Office of Government-wide Policy identity Assurance and Trusted Access Division

| Version Number | Date | Change Description |
| :----------: | :-------: | -------- |
| 1.0 | 1/5/21 | Initial Draft |
| 1.1 | 11/18/21 | Renumbered tables |

# Executive Summary

The Digital Worker Identity Playbook is a practical guide to manage digital worker identities. This playbook helps federal agency ICAM programs as well as CIO and CISO offices determine the risk of and define a process for digital worker identity management. A digital worker is an automated, software-based tool, application, or agent that performs a business task or process similar to a human user and uses Artificial Intelligence (AI) or other autonomous decision-making capabilities. OMB memo 19-17 requires agencies to ensure the digital identity of automated technologies are “distinguishable, auditable, and consistently managed.” However, agencies face implementation challenges when establishing identities for digital workers. Most often, they attempt to use human worker processes, which may hinder digital worker creation or access. Common challenges include:
-	Human worker identity attributes that do not apply to a digital worker. For example, some agencies create ad hoc digital worker identity attributes based on requirements for human users, some of which do not apply (e.g., work station location). Conversely, the scope of identity attributes required for human users may not include some attributes that are needed for digital workers (e.g., custodian names).
-	Lack of ability to provision individual user accounts to a digital worker. Some agencies allow digital workers to run on service, system, or group accounts. This is  because implementation teams are either unable or not authorized to have individual user accounts assigned to a digital worker. However, digital workers are less distinguishable from other non-person entity types when they use service, system, or group accounts rather than user accounts.

**Agencies should tailor this playbook to fit their mission, business, technology, and security needs and integrate into enterprise identity management policies.**

Federal agencies use digital workers to automate processes, increase efficiencies, and discover insights from large volumes of data. Digital workers may interact with or use sensitive information to perform unattended, high-risk tasks, which  may critically impact an agency's mission. Agencies usually leverage existing, human-based processes to create a digital worker identity, but this may hinder a digital worker's access or success. This playbook addresses the challenges in determining digital worker risk and outlines a process to establish a digital worker identity.

This playbook is iterative, and agencies are encouraged to collaborate, share best practices, and share lessons learned. Federal employees may consider joining a relevant committee or community of practice to learn and engage in digital worker identity management. 

-	[Identity, Credential, and Access Management subcommittee (ICAMSC)](https://community.max.gov/pages/viewpage.action?pageId=234815732){:target="_blank"}{:rel="noopener noreferrer"}
-	[Robotic Process Automation Community of Practice](https://digital.gov/communities/rpa/){:target="_blank"}{:rel="noopener noreferrer"}
-	[Artificial Intelligence Community of Practice](https://digital.gov/communities/artificial-intelligence/){:target="_blank"}{:rel="noopener noreferrer"}

## Key Terms 

These are key terms used throughout this document.

-	**Digital Worker** - An automated, software-based tool, application, or agent that performs a business task or process similar to a human user and uses AI or other autonomous decision-making capabilities.[^1] 

The list below includes the most common types of digital workers.

-	**Artificial Intelligence (AI)** - A computer system's ability to make autonomous decisions or perform tasks, traditionally requiring human intelligence.
-	**Chatbot** - A software tool that interacts with a human user to provide a service, such as retrieving data, answering a question, or directing the user to a resource.
-	**Machine Learning (ML)** - The process of teaching computers to learn from data and perform tasks with minimal direct instruction or programming on how to achieve the desired outcome.

## Disclaimer 

This playbook was developed by the General Services Administration Office of Government-wide Policy with input from federal IT practitioners. This document shouldn’t be interpreted as official policy or mandated action, and doesn’t provide authoritative definitions for IT terms. Instead, this playbook supplements existing federal IT policies and builds upon the Office of Management and Budget (OMB) Memorandum 19-17 (M-19-17), Enabling Mission Delivery through Improved Identity, Credential, and Access Management and existing federal identity guidance and playbooks. Subject areas with intersecting scope, such as the ethical use and development of digital workers, are considered only to the extent that they relate to digital identity management and credentialing for digital workers. Specific security control implementations are out of scope of this playbook, as are any elements of data protection requirements and the suitability process for a digital worker sponsor and custodian.

# A Three-Step Process for Digital Worker Identity Management

The three-step process outlined below is a structured, iterative approach with discrete actions to create a digital worker identity management process. _CIO and CISO offices_ are the intended audience for this guide. Use this guide to write, update, or enhance existing enterprise identity management policies. Agencies are encouraged to tailor these steps to meet organizational structures, unique requirements, and mission needs. 

[![A three part arrow diagram that includes 1 Determine the Impact, 2 Create an Identity, and 3 Provision an Identity. Below 1 Determine the impact is text that lists 1.1 Ensure Proper Oversight, 1.2 Score Risk Impact, and 1.3 Determine Adverse Impact Level. Below 2 Create an Identity is text that lists 2.1 Assign a Sponsor and Custodian and 2.2 Validate Worker Access. Below 3 Provision an Identity is text that lists 3.1 Capture and Store Identity Management Data Elements and 3.2 Capture and Store Identity Governance Data Elements.]({{site.baseurl}}/assets/playbooks/dw-process.png)]({{site.baseurl}}/assets/playbooks/dw-process.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 1. A Three-Step Process for Digital Worker Identity Management</b></p>

[Step 1. Determine the impact](#step-1-determine-the-impact) to decide whether to establish a digital worker identity. Much like the human worker, a digital worker should undergo a similar vetting process before being granted network or application access. Not all digital workers may require a unique identity. Work with the agency's ICAM governance structure[^2] to:
-	Create or expand the agency ICAM governance structure and policies for digital worker identity management oversight;
-	Score risk using the Digital Worker Impact Assessment; and
-	Identify a digital worker adverse impact level.[^3] 

The Digital Worker Impact Evaluation Matrix is a scoring tool. It uses six factors to score the risk of a digital worker's scope and access. Agencies can use the risk score to determine an overall adverse impact level. 

{% include alert-info.html heading="Key Point" content="Agencies may decide that digital workers with low adverse impact levels do not require a digital identity. If an agency’s policy demands that all digital workers require a digital identity, they should follow the Moderate level process." %}

[Step 2. Create an identity](#step-2-create-an-identity) that complies with the agency ICAM policies. A digital worker is assigned a sponsor and custodian that maintains the digital worker processes. The sponsorship process creates and assigns digital worker oversight roles and responsibilities for a sponsor and a custodian. After appointing a sponsor and custodian, follow security best practices when validating a digital worker level of access. Best practices include employing least privilege, separation of duties, and regular access recertification, similar to human workers.

[Step 3. Provision an identity](#step-3-provision-an-identity) in the agency enterprise identity management systems. After assigning a sponsor, custodian, and validating access, capture the appropriate data elements in the digital worker identity record. These data elements enable the agency to appropriately catalog and monitor digital workers through the identity lifecycle.

This playbook should aid agencies in integrating digital worker identity management processes into existing enterprise identity management policies.

[![A three part arrow diagram that includes 1 Determine the Impact, 2 Create an Identity, and 3 Provision an Identity. 1 Determine the Impact is highlighted.]({{site.baseurl}}/assets/playbooks/dw-step-one.png)]({{site.baseurl}}/assets/playbooks/dw-step-one.png){:target="_blank"}{:rel="noopener noreferrer"}

# Step 1. Determine the Impact

Ensure digital worker identity management has proper governance, score the function of the digital worker across six categories, and then use the risk score to arrive at an adverse impact level. For this step, we use the Digital Worker Impact Evaluation Matrix (Table 1).

## 1.1 Ensure Proper Oversight 

The ICAM governance structure ensures enterprise identity management policies are updated to include digital worker management and use. For ICAM oversight and program management examples, see the [ICAM Program Management Playbook](https://playbooks.idmanagement.gov/pm/){:target="_blank"}{:rel="noopener noreferrer"}.

<p align="center"><b>Update the agency enterprise identity management policies to include digital worker identity management.</b></p>

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <td class="tg-0pky">Governance<br>Collaboration<br>Example</td>
    <td class="tg-0pky">Before creating and provisioning a digital worker, the agency ICAM<br>governance structure can collaborate with Information System Security<br>Officers on digital worker identity management. Collaboration may<br>include:<br><br> 
      
      ● Verifying digital worker security and non-functional requirements<br>
      ● Security and privacy assessments<br>
      ● Executable, vulnerability and other scans<br>
      ● Digital worker logic and decision-making design documents
    </td>
  </tr>
</thead>
</table>

## 1.2 Score Risk Impact 

A risk score is calculated across six factors based on worker autonomy, content handled, type of access, and privileges required.

Each factor has an associated score, and the sum of these six-factor scores is the overall impact score. If multiple criteria within a factor apply to a digital worker, agencies should select the criterion with the highest score.

**Table 1. Digital Worker Impact Evaluation Matrix**[^4]

| Score each factor based on the most applicable scenario |     | 
| ------------------------ | ------------ | 
| **Factor 1 - Is the digital worker attended or unattended?** | **Score** | 
| ● Attended | 0 | 
| ● Unattended | 10 |
| **Factor 2 - What is the highest level of data access by the digital worker?** |     | 
| ● Data available to the public (either without a user account or with unvetted user account) | 0 | 
| ● Agency operational data, controlled unclassified information (CUI), or data on individuals in low volumes. Doesn’t contain personally identifiable information (PII) or personal health information (PHI). | 5 |
| ● PII and/or PHI | 55 | 
| ● Agency critical operational data or data that could impact life, health, or safety of individuals/systems relied upon for health and safety; or very high volumes of agency operational data | 90 |
| **Factor 3 - Does the digital worker have access to internal and/or external networks?** |     | 
| ● No internal intranet or external Internet connection | 0 | 
| ● Either internal intranet access only OR external Internet access (not both) | 5 |
| ● Internal and external network access (i.e., Internet and intranet) | 10 | 
| **Factor 4 - What is the impact of the digital worker output?** |     | 
| ● Output impacts general internal business operations, but not for critical processes or decisions | 5 | 
| ● Output impacts outside organizations in general business operations or public reporting (e.g., public facing websites or chatbots), but not for critical processes or decisions | 25 |
| ● Output impacts mission critical organization operations of the agency or other organizations, health or safety of individuals, national economic stability, national security, critical infrastructure, or similarly consequential operations | 90 | 
| **Factor 5 - What type of system account privileges does the digital worker require?** |     | 
| ● No system accounts used | 0 | 
| ● Standard system account(s) (roles limited by the business function) | 10 |
| ● System admin account (privileged access) | 35 | 
| ● Multiple system admin accounts (multiple privileged access roles) | 40 |
| **Factor 6 - Does the digital worker act on its own insights?** |     | 
| ● Digital worker develops insights, but doesn’t take action on its insights | 0 | 
| ● Digital worker develops insights and acts on the insights after human review | 5 |
| ● Digital worker develops insights and acts on the insights without human review or approval before the action is taken | 10 | 

## 1.3 Determine Adverse Impact Level 

The adverse impact level is the potential magnitude of harm a digital worker can cause the organization, assets, individuals, other organizations, and the United States' economic and national security interests. Specific impacts include: 
-	unauthorized disclosure;
-	change or destruction of information;
-	harm or endangerment of human life;
-	loss of access to information systems; or 
-	damage to high-value assets.

The four adverse impact levels represent a different scale of harm a digital worker may cause.
-	Low;
-	Moderate; 
-	High; and 
-	Critical. 

{% include alert-info.html heading="Key Point" content="The Potential Adverse Impact Levels are grounded in NIST Special Publication 800-30 and are a recommendation. Agencies may adjust or tailor the levels to fit their individual risk levels or descriptions." %}

**Table 2. Potential Adverse Impact Levels**

| Impact Score | Potential Adverse Impact | Description |
| ------------------------ | ------------ | ------------------ |
| 0-35 | **Low** | Effects of an error or accident are minimal, resulting in negligible, if any, impacts on organizational operations, finances, assets, individuals, other organizations, or the nation. |
| 36-55 | **Moderate** | Effects of an error or accident are limited and may result in minor or temporary impact on organizational missions/business functions, organizational assets, or the nation. This includes increased difficulty in performing business operations in a timely manner, with sufficient confidence, or within planned resource constraints; minor damage to agency image, reputation, or trust; minor financial loss to the agency or other organizations; and/or noncompliance with applicable laws or regulations. |
| 56-90 | **High** | Effects of an error or accident are wide-ranging and could result in serious or long-term impact on organizational missions/business functions, organizational assets, or the nation. This includes significant financial losses for the agency; substantially reduced capacity to conduct mission critical business; loss of PII, Business Identifiable Information, or PHI; and/or damage to agency image or reputation. |
| 91+ | **Critical** | Effects of an error or accident are extensive and will have severe or catastrophic impact on organizational missions/business functions, assets, or the nation. This includes major financial losses for the agency or other organizations, loss of government continuity of operations or ability to conduct mission critical business, life-threatening injury or loss of life, and/or harm to national security. |

[![A three part arrow diagram that includes 1 Determine the Impact, 2 Create an Identity, and 3 Provision an Identity. 2 Create an Identity is highlighted.]({{site.baseurl}}/assets/playbooks/dw-step-two.png)]({{site.baseurl}}/assets/playbooks/dw-step-two.png){:target="_blank"}{:rel="noopener noreferrer"}

# Step 2. Create an Identity

Once your agency has determined the digital worker’s level of potential adverse impact, a digital worker identity is created, if needed. The identity process includes sponsorship and validation activities based on the adverse impact level from Step 1. 

## 2.1 Assign a Sponsor and Custodian 

The sponsorship process allows agencies to assign specific roles and responsibilities for oversight of digital workers. The agency’s ICAM governance structure ensures the sponsorship process actions are completed; however, it is up to the individual agencies to define how a sponsor and custodian are assigned. 

**Table 3. Sponsor and Custodian Responsibilities**

| Role | Description | Responsibilities |
| -------------------- | ------------ | ------------------ |
| Sponsor | ● Responsible for digital worker compliance; and<br>● A federal government employee. | ● Assign roles and responsibilities to govern the digital worker, such as a primary and backup custodian; <br>● Field digital worker inquiries from agency or other government entity leaders; and<br>● Oversee who has access to the digital worker. |
| Custodian | ● Responsible for digital worker day-to-day operational management; and<br>● A federal government employee or contractor. | ● Hold a comparable level of access as the digital worker;<br>● Complete initial and routine training in digital worker management and security;<br>● Rotate digital worker password or authenticators;<br>● Maintain digital worker access;<br>● Oversee retraining or tuning of an underlying model; and<br>● Track and monitor digital worker data input and output. |

### Industry Best Practice

Recertification or access reviews are assessed periodically if access privileges are still needed to complete a task and a minimum recommendation is required to  verify and validate access. The recommended intervals in Table 4 for sponsor and custodian acknowledgment should be considered a minimum acceptable standard. Agencies may adjust the recertification frequency, but should meet or exceed the recommended intervals. When certifying human access to IT platforms, specific systems and applications may impact the frequency of necessary certifications. Agencies should assess the platforms that digital workers have access to and use this to help evaluate certification frequency.

{% include alert-info.html heading="Key Point" content="Agencies may decide that digital workers with low adverse impact levels do not require a digital identity. If an agency’s policy demands that all digital workers require a digital identity, they should follow the Moderate level process." %}

**Table 4. Sponsorship (SP) Process**

| &nbsp;&nbsp;&nbsp;ID[^5]&nbsp; | Action&nbsp;&nbsp;&nbsp; | Low | Moderate | High | Critical |
| ----------- | ------------ | ----------- | :------------: | :-----------: | :------------: |
| SP-1 | **Document a business need for the digital worker.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b> |
| SP-2 | **Assign an organizational sponsor for the digital worker.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b><br>Suggested CIO, CISO, or equivalent |
| SP-3 | **Sponsor acknowledges responsibility for the digital worker on an initial and routine basis.** | N/A | <b>✓</b><br>Recertify sponsor annually | <b>✓</b><br>Recertify sponsor annually | <b>✓</b><br>Recertify sponsor every six months |
| SP-4 | **Sponsor assigns the custodian of the digital worker.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b> |
| SP-5 | **Notify the custodian of his or her responsibility by the sponsor.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b> |
| SP-6 | **Confirm the custodian acknowledges responsibility for the digital worker on an initial and routine basis.** | N/A | <b>✓</b><br>Recertify custodian annually | <b>✓</b><br>Recertify custodian annually | <b>✓</b><br>Recertify custodian every six months |

## 2.2 Validate Worker Access 

Validation actions record the activities to ensure the digital worker continues to behave as expected throughout its lifecycle. The agency’s ICAM governance structure is responsible for ensuring the validation process actions are completed and tracked, but the individual agencies must define a process that fits the agency's mission needs and requirements. Validation is based on the following factors as a starting point. Agencies may include other mission specific review factors as needed. 

1.	**Employ least privilege (VD-1).** Like a human worker, a digital worker should have the lowest access required to complete its task. The sponsor should review the use of an elevated account before initially granting it or upgrading an account already in use.
2.	**Separation of duties (VD-2)** is a principle that prevents any single person or entity from completing all the functions in a critical or sensitive process. It is designed to “prevent fraud, theft, and errors.” The sponsor should review that the digital worker role does not create a separation of duty conflict. If there is a conflict, document the exception.
3.	**Code review (VD-3).** Digital worker code may include worker logic and decision-making processes. Include design or other system documentation as part of code review for reasoning and decision-making intent.
4.	**Ethics and bias review (VD-4 and VD-5).** While government-wide standards for ethics and bias are in development, agencies should define their own ethics standards or collaborate with other agencies that align with the agency mission.
5.	**Recertification acknowledgement (VD-6 and VD-7).** Recertification is the act of reviewing access on a periodic basis. It should occur on an annual or bi-annual schedule based on the adverse impact level.

{% include alert-info.html heading="Key Point" content="Existing validation activities can be leveraged and integrated into the digital worker validation process. Even though there are no activities for low impact, reassess a digital worker impact level every time there is a code change or update to ensure the impact level has not changed." %}

Use Table 5 for specific validation actions aligned with adverse impact level.

**Table 5. Validation (VD) Process**

| &nbsp;&nbsp;&nbsp;ID&nbsp;&nbsp; | Action&nbsp;&nbsp;&nbsp; | Low | Moderate | High | Critical |
| ----------- | ------------ | ----------- | :------------: | :-----------: | :------------: |
| VD-1 | **Validate the digital worker role employs least privilege necessary to accomplish its task.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b> |
| VD-2 | **Validate the digital worker role doesn’t create separation of duty conflicts for the digital worker or any human users.** | N/A | <b>✓</b> | <b>✓</b> | <b>✓</b> |
| VD-3 | **Validate the digital worker has undergone a code review prior to release. Additional code reviews are required for any code changes at higher impact.** | N/A | <b>✓</b><br>Following major changes to code | <b>✓</b><br>Following any changes to code | <b>✓</b><br>Following any changes to code |
| VD-4| **Validate the digital worker has undergone review of ethics according to applicable government and/or agency standards** | N/A | N/A | <b>✓</b><br>Conduct initial review and annual periodic review | <b>✓</b><br>Conduct initial review and periodic review every six months |
| VD-5 | **Validate the digital worker has undergone review for bias according to applicable government standards.** | N/A | <b>✓</b><br>Conduct initial bias review | <b>✓</b><br>Conduct initial bias review and annual periodic review | <b>✓</b><br>Conduct initial bias review and periodic review every six months |
| VD-6 | **Validate the sponsor has recertified acknowledgement of responsibility for the digital worker at required intervals.** | N/A | <b>✓</b><br>Verify sponsor recertification annually | <b>✓</b><br>Verify sponsor recertification annually | <b>✓</b><br>Verify sponsor recertification every six months |
| VD-7| **Validate the custodian has recertified acknowledgement of responsibility for the digital worker at required intervals.** | N/A | <b>✓</b><br>Verify custodian recertification annually | <b>✓</b><br>Verify custodian recertification annually | <b>✓</b><br>Verify custodian recertification every six months |

{% include alert-info.html heading="Key Point" content="SP-3 is a similar but separate activity than VD-6. In SP-3 the sponsor acknowledges their role and responsibilities initially and reacknowledges them every six months. VD-6 is validation of the acknowledgement. Perform each action together or separately, but they are tracked separately for flexibility." %}

{% include alert-info.html heading="Key Point" content="VD-3, VD-4, and VD-5 are validating the code, ethics, and bias reviews that have been conducted. It is up to the individual agencies to ensure a standard for conducting such reviews is followed. Agency representatives, such as the sponsor or custodian, should collaborate within a community of practice to capture best practices on how to perform the various reviews in Step 2.2." %}

[![A three part arrow diagram that includes 1 Determine the Impact, 2 Create an Identity, and 3 Provision an Identity. 3 Provision an Identity is highlighted.]({{site.baseurl}}/assets/playbooks/dw-step-three.png)]({{site.baseurl}}/assets/playbooks/dw-step-three.png){:target="_blank"}{:rel="noopener noreferrer"}

# Step 3. Provision an Identity

Capture the appropriate digital worker data elements. These attributes are stored in the agency IDMS or other systems.

## 3.1 Capture and Store Identity Management Data Elements 

_Identity management system data elements_ are identification and sponsorship elements. They include information to uniquely identify a digital worker or whom to contact for more details. Agencies usually store Identity management data elements in an identity management system or directory and should be required for any digital worker with a unique identity regardless of adverse impact level. Table 6 provides guidance and recommended data fields to capture the necessary digital worker identity elements.

**Table 6. Identity Management System (IDMS) Data Fields**

| &nbsp;&nbsp;&nbsp;ID&nbsp;&nbsp;&nbsp; | IDMS Field Name&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Field Type | Additional Guidance |
| ----------- | ------------ | ----------- | ------------ | 
| DF-1 | **Digital Worker**<br>_(new field)_ | Boolean<br>_e.g., Checkbox, True/False, yes/no, etc._ | _Denote if this is (Yes/True) or is not (No/False) a digital worker._ |
| DF-2 | **Agency unique user ID**<br>_(existing field)_ | Text<br>_Recommend using “DW” or other uniqueness element followed by the identifier based on agency naming conventions._ | _Use a distinguishing and standard naming convention for digital workers. This isn’t a card holder unique identifier (CHUID) or related to PIV._ |
| DF-3 | **First Name** and<br> **Last Name**<br>_(existing fields)_ | Text<br>_**First name:** group function<br>**Last name:** “DW” followed by a numerical value_ | _Use agency naming convention if IDMS requires first and last name. The first name field should be completed with the group function (e.g., Technology Division, CFO) and the last name field should be completed with “DW” followed by a numerical value corresponding with the sequential order in which the digital worker was built within the associated group function._ |
| DF-4 | **Digital Worker Sponsor Name**<br>_(new field[s])_ | Text<br>_Recommend the individual’s full name (generally first and last name)_ | _Specify the sponsor of the digital worker._ |
| DF-5 | **Digital Worker Custodian Name**<br>_(new field[s])_ | Text<br>_Recommend the individual’s full name (generally first and last name)_ | _Specify the custodian of the digital worker._ |
| DF-6 | **Digital Worker Description**<br>_(optional new field)_ | Text (250)<br>_Recommend including a brief description of the digital worker (e.g., the type of AI used, the purpose, and actions of the digital worker)_ | _Provide a short description of what the digital worker does and the type of digital technology used._ |
| DF-7 | **Responsible Organization**<br>_(optional new field)_ | Text<br>_Include the name of the organization according to the official agency organizational chart_ | _Specify the name of the responsible agency organization or group._ |

## 3.2 Capture and Store Identity Governance Data Elements 

_Identity governance data elements_ validate and recertify access. They include information used to report on digital worker access and  include information on:

-	Acknowledgment date;
-	Recertification date;
-	Adverse impact level; and
-	Other completion or acknowledgment dates.

Agencies may store and track identity governance data elements in an existing system like an identity governance or directory management tool. The agency should develop an appropriate method or process to track these elements if one doesn’t exist.

**Table 7. Identity Governance Data Elements**
 
| &nbsp;&nbsp;ID&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Data Element | Additional Guidance |
| ----------- | ------------ | ----------- | 
| DF-8 | **Digital Worker Sponsor Date of Last Acknowledgement** | _Specify the date the sponsor acknowledged responsibility for the digital worker. Recommend including the date in the format specified by agency guidelines (e.g., 01/01/2020)._ |
| DF-9 | **Digital Worker Date of Sponsor Acknowledgement Recertification**<br>_(optional)_ | _Track when the sponsor acknowledgement must be recertified. This can be tracked as a formula based on the last acknowledgement date and adverse impact level requirements, or a format and method specified by agency guidelines._ |
| DF-10 | **Level of Potential Adverse Impact** | _Specify the level of potential adverse impact as determined using the methodology in section 3.2 of this document. Limited response (e.g., “Low”, “Moderate,” “High,” or “Critical”)._ |
| DF-11 | **Digital Worker Date of Last Custodian Acknowledgement** | _Specify the date the custodian acknowledged responsibility for the digital worker. Recommend including the date in the format specified by agency guidelines (e.g., 01/01/2020)._ |
| DF-12 | **Digital Worker Date of Custodian Acknowledgement Recertification**<br>_(optional)_ | _Track when the custodian acknowledgement must be recertified. This can be tracked as a formula based on the last acknowledgement date and adverse impact level requirements, or a format and method specified by agency guidelines._ |
| DF-13 | **Approved Source Internet Protocol (IP) Address Range**<br>_( only for High and Critical)_ | _Specify the range of source IP addresses on which the digital worker may operate._ |
| DF-14 | **Code Review Completion Date**<br>_(optional)_ | _Specify the code review completion date (refer to VD-3 for more details). Recommend including the date in the format specified by agency guidelines (e.g., 01/01/2020)._ |
| DF-15 | **Ethics Review Completion Date** | _Specify the digital worker ethics review completion date (refer to VD-4 for more details). Recommend including the date in the format specified by agency guidelines (e.g., 01/01/2020)._ |
| DF-16 | **Next Ethics Review Date**<br>_(optional)_ | _Track when the next ethics review date must be conducted. This can be tracked as a formula based on the last ethics review date and adverse impact level requirements, or a format and method specified by agency guidelines._ |
| DF-17 | **Digital Worker Bias Review Completion Date** | _Specify the digital worker bias review completion date (refer to VD-5 for more details). Recommend including the date in the format specified by agency guidelines (e.g., 01/01/2020)._ |
| DF-18 | **Next Bias Review Date**<br>_(optional)_ | _Track when the next bias review date must be conducted. This can be tracked as a formula based on the last bias review date and adverse impact level requirements, or a format and method specified by agency guidelines._ |

# Conclusion

[text here]

# Appendix A. Digital Worker Impact Evaluation Factors

[text here]

# Appendix B. Critical Case Study

[text here]

# Appendix C. Low Case Study

[text here]

# Footnotes

[text here]

