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
    href: '#Step-2-create-an-identity'
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

# Step 1. Determine the Impact

[text here]

## 1.1 Ensure Proper Oversight 

[text here]

## 1.2 Score Risk Impact 

[text here]

## 1.3 Determine Adverse Impact Level 

[text here]

# Step 2. Create an Identity

[text here]

## 2.1 Assign a Sponsor and Custodian 

[text here]

## 2.2 Validate Worker Access 

[text here]

# Step 3. Provision an Identity

[text here]

## 3.1 Capture and Store Identity Management Data Elements 

[text here]

## 3.2 Capture and Store Identity Governance Data Elements 

[text here]

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

