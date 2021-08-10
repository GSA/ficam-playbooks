---
layout: page
collection: playbooks
title: Privileged User Playbook
type: Markdown
pubdate: 09/2021
permalink: /playbooks/pam/
description: This document provides federal agencies with guidance to manage its privileged users by mitigating the inherent risks associated with this population through the use of Identity, Credential, and Access Management (ICAM).
sticky_sidenav: true
sidenav: playbook-pam

subnav:
    - text: Executive Summary
      href: '#executive-summary'
    - text: Protect Federal Identities and Logical Assets
      href: '#protect-federal-identities-and-logical-assets'
    - text: Step 1. Develop Program Goals
      href: '#step-1-develop-program-goals'
    - text: Step 2. Define and Identify
      href: '#step-2-define-and-identify'
    - text: Step 3. Integrate into ICAM
      href: '#step-3-integrate-into-icam'
    - text: Step 4. Prioritize and Execute
      href: '#step-4-prioritize-and-execute'
    - text: Appendix A. Reference Documents
      href: '#appendix-a-reference-documentation'
    - text: Appendix B. Privileged User Agreement
      href: '#appendix-b-privileged-user-agreement'
    - text: Appendix C. Privileged Account DIRA
      href: '#appendix-c-privileged-account-dira'
    - text: Appendix D. 800-53 Privileged User Overlay
      href: '#appendix-d-nist-sp-800-53-privileged-user-overlay'
---

{% assign categories = "" | split: "" %}
{% for pam in site.data.overlay_pam %}
  {% assign category = pam.category | strip %}
  {% assign categories = categories | push: category | uniq | sort %}
{% endfor %}
{% assign categories = categories | uniq | sort %}

<a href="../../assets/img/logo-gsa.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-gsa.png" width="64" height='64' align="left" alt="U.S. General Services Administration Logo"></a>
<a href="../../assets/img/logo-cioc.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-cioc.png" width="64" height='64' align="left" alt="U.S. Federal Chief Information Officer Council Logo"></a>

[![General Services Administration Logo]({{site.baseurl}}/assets/img/logo-gsa.png){:style="width:50%;float:left;"}]({{site.baseurl}}/assets/img/logo-gsa.png){:target="_blank"}{:rel="noopener noreferrer"} [![Federal CIO Council Logo]({{site.baseurl}}/assets/img/logo-cioc.png){:style="width:50%;float:left;"}]({{site.baseurl}}/assets/img/logo-cioc.png){:target="_blank"}{:rel="noopener noreferrer"}[![Department of Homeland Security Cybersecurity and Infrastructure Security Agency Logo]({{site.baseurl}}/assets/img/logo-cisa.png){:style="width:16px;height:16px;float:left;"}]({{site.baseurl}}/assets/img/logo-cisa.png){:target="_blank"}{:rel="noopener noreferrer"}

Version 1.0  
Last Updated: August xx, 2021

# Executive Summary
The Privileged User Playbook is a practical guide to **help federal agencies implement and manage a privileged user program**. Privileged users are a special user type that perform security-related duties. A privileged user program enables an agency to identify, track, monitor, and audit privileged users and accounts, effectively decreasing the cyber risk and impact on an agency's mission. **Unwanted behavior or compromise of privileged accounts are also responsible for the most high-profile federal security breaches**. It is a critical Identity, Credential, and Access Management capability to identify privileged users and access to high value assets. As part of agency insider threat programs, agencies can use this playbook to define privileged user program requirements and capabilities.

There are three main use cases to identify a privileged account or user.
1. Accounts used to manage IT infrastructure and resources of high value assets (HVA) and core systems (e.g. perform maintenance activities on human resource applications or databases).
2. Help desk personnel with escalated privilege to perform security-relevant processes on endpoints (e.g. install software on user laptops or change endpoint configuration settings).
3. Managers that approve access or accounts (e.g. a manager approving access requests to a risk reporting application).

Privileged users are managed as a distinct and separate identity to decrease the risk and impact to agencies mission.
1. These employees and contractors have the ability to jeopardize sensitive information or infrastructure, whether knowingly or unknowingly.
2. Privileged users have the potential to compromise all three core elements of information security: availability, confidentiality, and integrity.

Agencies can use this playbook to help plan and implement a logical privileged user program following government-wide best practices. This playbook includes a four step process aligned with the [Federal Identity, Credential, and Access Management (ICAM) Architecture](https://playbooks.idmanagement.gov/arch/){:target="_blank"}{:rel="noopener noreferrer"} and is designed for **insider threat, ICAM, and risk management professionals interested in identifying best practices for mitigation privileged user risk** for new or existing privileged user programs. Agencies are encouraged to tailor this playbook to fit their unique organizational structure, mission needs, and requirements. Other IT program participants, including cybersecurity program managers, may find value in incorporating this playbook approach in their planning.

## Key Terms
These are key terms used throughout this document.
- **Account Compromise** is the unauthorized use of an account including disclosure, modification, substitution, or use of sensitive information.
- **[Insider Threat](https://csrc.nist.gov/glossary/term/insider_threat){:target="_blank"}{:rel="noopener noreferrer"}** is the potential for an insider will use her/his authorized access, wittingly or unwittingly, to do harm to the security of United States. This threat can include damage to the United States through espionage, terrorism, unauthorized disclosure of national security information, or through the loss or degradation of departmental resources or capabilities.
- **[Functional Privileged User](https://playbooks.idmanagement.gov/docs/playbook-dira.pdf){:target="_blank"}{:rel="noopener noreferrer"}** can access information resources provided by the application and approval workflows such as approving access requests.
- **[Privileged Account](https://csrc.nist.gov/glossary/term/privileged_account){:target="_blank"}{:rel="noopener noreferrer"}** is a system account used by a privileged user. A privileged account can belong to a single endpoint, domain, database, or application.
- **Privileged Compromise** is either an adverse action of a privileged user or account through either an insider threat or an account compromise.
- **[Privilege Escalation](https://csrc.nist.gov/glossary/term/privilege_escalation){:target="_blank"}{:rel="noopener noreferrer"}** is the exploitation of a bug or flaw that allows for a higher privilege level than what would normally be permitted.
- **[Privileged User](https://csrc.nist.gov/glossary/term/privileged_user){:target="_blank"}{:rel="noopener noreferrer"}** is a user that is authorized (and therefore, trusted) to perform security-relevant functions that ordinary users are not authorized to perform. Also known as a Privileged IT User, Privileged Network User or [Superuser](https://csrc.nist.gov/glossary/term/superuser){:target="_blank"}{:rel="noopener noreferrer"}.

## Disclaimer
This playbook in informative. It was developed by the General Services Administration Office Government-wide Policy (GSA OGP) in collaboration with the Department of Homeland Security (DHS) Continuous Diagnostic and Mitigation (CDM) Program with input from federal identity and security practitioners. This playbook is limited to high-level guidance that is specific to privileged users accessing federal government information systems. This playbook shouldn’t be interpreted as official policy or mandated action, and doesn’t provide authoritative definitions for IT terms. Where appropriate, key terms from the National Institute for Standards and Technology (NIST) or Federal Information Security Management Act (FISMA) are used. This playbook supplements existing Federal IT policies and builds upon the [Office of Management and Budget Memorandum 19-17 - Enabling Mission Delivery through Improved Identity, Credential, and Access Management](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}{:rel="noopener noreferrer"}, as well as existing Federal identity guidance and playbooks.

# Protect Federal Identities and Logical Assets
Government employees and contractors need elevated access to perform necessary administrative and security functions, yet this carries an inherent risk of insider threat or account compromise. As a result, agencies should implement privilege user controls that mitigate this risk without impeding their ability to carry out assigned job duties. In creating a secure physical and virtual workplace for privileged users, agencies align efforts with the [FICAM Architecture](https://playbooks.idmanagement.gov/arch/){:target="_blank"}{:rel="noopener noreferrer"}.

This playbook provides informative guidance to manage federal employee and contractor privileged users by mitigating the inherent risks associated with this population. An agency achieves this outcome through the use of ICAM services. The following are the four primary steps to establish or enhance an agency's privileged user program.
1. [Define and Identify](#2-define-and-identify) privileged roles as those accounts that have elevated access to an agency's resources. Privileged accounts can be anywhere across a network or system and should be tracked and audited on a regular basis.
2. [Develop Program Goals](#1-develop-program-goals) to identify the potential impact and risk to your agency's mission. It is crucial that an agency understand why a privileged user program is important and the risks associated with elevated access. Mitigate privileged user risk from engaging in unwanted behavior or compromise. Scope program outcomes of mitigating risk toward the impact in achieving the agency mission. This step also includes engaging agency stakeholders and potentially government-wide groups.
3. [Integrate into ICAM](#3-integrate-into-icam) for a holistic management approach. Implementing ICAM best practices as well as additional countermeasures to prevent privileged user and account misuse, abuse, or compromise can provide comprehensive, integrated protection of agency resources.
4. [Prioritize and Execute](#4-prioritize-and-execute) on your plan. Like most IT initiatives, this is a journey. Threats change. Based on your agency risk, this may require a multi-year plan to add capabilities and services. An agency should leverage existing efforts to achieve information security goals by directing or tailoring playbook steps based on its resources, environment, mission, business needs, and privileged user population.

{% include alert-info.html heading="Is this Privileged Access Management or Account Security" content="Different vendors may use a different terms for their product. Some vendors may use the term Privileged Access or Account Management (PAM), Privileged Identity Management (PIM), Privileged Security, or something in-between. For the intent of this playbook, the agnostic privileged user is used to encompass all service areas of ICAM." %}

[![An end user account can be compromised to esclate privileges in a domain takeover]({{site.baseurl}}/assets/playbooks/pam-journey-map.png)]({{site.baseurl}}/assets/playbooks/pam-journey-map.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 1. Develop Program Goals
Privileged compromise of an agency's privileged user population can significantly compromise an agency’s mission. An agency should be fully aware of the potential for risk involved in not managing a privileged user population that can lead to catastrophic events such as:
- exfiltration of sensitive or classified data;
- rendering a system inoperable through configuration change; or
- creating and granting shadow administrator accounts for persistent access.

Privileged compromise comes in two flavors:
1. Insider threat or
2. Account compromise

### Insider Threat
Insider threat is the accidental, complacent, or malicious actions of a government employee or contractor. A privileged user program is grounded in implementing, monitoring, and reporting on insider-based threats. The below table provides the definition and indicators or insider threat classifications.

| Insider Threat Classification | Definition | Example |
| --------------------- | -------------- | ------------ |
|   **Accidental**  |   Lack of awareness regarding policies, procedures, and technical competencies. | 1. Unknowingly install software that is not approved for use.<br>2. Use privileged accounts for anything other than official administrative actions.<br>3. A privileged user accidentally deletes all data with a single command. |
|   **Complacent**  |   Overall lax or careless approach to security. | 1. Create user accounts and assign privileges without the appropriate review and approval.<br>2. Share system account passwords. |
|   **Malicious**   |  Intentionally disrupt, threaten, or endanger an organization’s activities or assets. | 1. Unwanted, purposeful disclosure or theft of information.<br>2. Introduce malicious code, malware, Trojan horse, viruses.<br>3. Destroy or modify system audit logs. |

Each category of insider threat is further linked to an unwanted behavior.

| Unwanted Behavior | Definition | Example |
| ----------------- | ---------- | ------- |
| **Fraud** | Unwanted use, modification, addition, or deletion of agency’s data for personal gain.| On the pretense of fixing corrupt data, a database administrator modifies data without authorization.|
| **Espionage** | Sharing restricted information with the intention of aiding a foreign actor or harming the U.S. Government. |  System administrator uses elevated access to retrieve confidential data and sells it to a foreign actor.|
| **Sabotage** | Purposefully inflicting harm on an organization.| Maintenance worker inserts a Universal Serial Bus (USB) drive into a server to inject malware on behalf of an external bad actor.|
| **Intellectual Property Theft**| Stealing intangible assets (e.g., discoveries, inventions, designs) from an organization.| Cloud administrator uses elevated access to server to steal proprietary information.|
| **Unwanted Information Disclosure**| A communication or physical transfer of information to a recipient who is not authorized to access to the information.| System administrator creates a “backdoor” account to inappropriately access and release classified information.|

Understanding insider threat classifications and unwanted behavior supports an agency’s implementation of a privileged user program. The procedural and technical measures operate in unison to mitigate the range of privileged users’ basis for unwanted behavior. Furthermore, the relationship between the three insider threat classifications and this playbooks aids an agency in the broader effort of fulfilling the insider threat mitigation requirements in the National Insider Threat Policy and relevant Executive Orders.

### Agency Governance

In most agencies, a PAM Program is subordinate to or interacts with multiple other agency programs.
- **High Value Asset** - [OMB Memo 19-03](https://www.whitehouse.gov/wp-content/uploads/2018/12/M-19-03.pdf){:target="_blank"}{:rel="noopener noreferrer"} outlines requirements to identify, track, and manage an agencies most critical assets. [Amplifying guidance from CISA](https://www.cisa.gov/sites/default/files/publications/Securing%20High%20Value%20Assets_Version%201.1_July%202018_508c.pdf){:target="_blank"}{:rel="noopener noreferrer"} recommended using unique accounts, logging key security events, and implementing multi-factor authentication for all HVA users, but particularly privileged users.
- **Insider Threat** - Include programs to detect and prevent the unauthorized disclosure of sensitive information. An insider threat program consists of capabilities that provide access to information; centralized information integration, analysis, and response; employee insider threat awareness training; and the monitoring of user activity on government computers.
- **Cybersecurity / ICAM** - Responsible for identity, credential, and access management services and coordination.
- **Continuous Diagnostic and Migration (CDM)** - Cybersecurity tools, integration services, and dashboards to help an agency reduce attack surface, increase visibility into cybersecurity posture, improve response, and streamline FISMA reporting.
- **Risk Management** - Identify and track implementation and operation of security controls.

{% include alert-info.html heading="Insider Threat Mitigation" content="Because of privileged users’ elevated access, unwanted behavior by these individuals can significantly compromise agency assets or operations. As a result, privileged user management is a cornerstone of insider threat mitigation." %}

### Program Objectives
Even though agency missions may differ, objectives of a privileged user program are fairly similar. The below strategic and tactical objectives are used as a starting point to plan a privileged user program.

- **Strategic Objectives**
1. Identify vulnerabilities and risk factors to protect high value assets and other assets.
2. Limit successful attacks by preventing network takeover and lateral movement.
3. Secure sensitive workloads both on-premise and in the cloud.
4. Prevent sensitive data loss and exfiltration.
5. Comply with existing and evolving federal requirements.

- **Tactical Objectives**
1. Inventory and validate privileged account scope and numbers.
2. Minimize the number of privileged users; 
3. Limit both duration of privileged account log-in and privileged account validity.
4. Enforce least privilege by limiting overall functions and the functions that can be performed remotely.
5. Ensure that privileged user activities are logged and audited on a regular basis.

{% include alert-info.html heading="Privileged Access Apply to Both People and Non-People" content="It is easy to overlook the impact of device and communication channel compromise. Consider objectives for both privileged people users and also non-people entities sometimes referred to as machine identities." %}

[![Consider both person and non-person access to protected resources]({{site.baseurl}}/assets/playbooks/pam-iceberg.png)]({{site.baseurl}}/assets/playbooks/pam-iceberg.png){:target="_blank"}{:rel="noopener noreferrer"}

In addition to setting minimum program objectives, an agency should evaluate the risks to its resources by conducting a [Digital Identity Risk Assessment (DIRA)](https://playbooks.idmanagement.gov/docs/playbook-dira.pdf){:target="_blank"}{:rel="noopener noreferrer"}. The DIRA process identifies the risk of user transactions and identifies a minimum identity assurance, authenticator assurance, and federation assurance level outlined in [NIST Special Publication 800-63-3](https://pages.nist.gov/800-63-3/sp800-63-3.html){:target="_blank"}{:rel="noopener noreferrer"}. An example of a [Privileged Account DIRA is located in Appendix C](appendix-c-privileged-account-dira).

### Zero Trust Alignment
NIST Special Publication 800-207 outlines a Zero Trust Architecture that move defenses from static, network-based perimeters to focus on users, assets, and resources. It shifts the operating model toward using telemetry to determine trust rather than location (e.g. if a user is on an agency netowrk and on a government furnished device, they are trusted). WIthin the context of this playbook, step 4 provides recommendations on how to align privileged program technical measures with a zero trust architecture from five elements.

1. User - The user includes both the privileged user and the privileged account. User characteristics used an an access decision may include identity assurance level, credential assurance level, and entitlements.
2. Device - The device can be assigned to a user or agnostic (a server, password vault, network device, etc.). Device characteristics used in an access decision may include operating system version, device type (government, personal, etc.), device format (mobile, tablet, laptop, etc.), agency compliance state, or location.  
3. Network - The network is agnostic to the method of accessing the data. This may include public internet or agency intranet. Network characteristics used in an access decision may include network type (public or private), network speed, and other indicators.
4. Application - The application is the method of serving the data. This can include a front-end application, a command line interface, a database, or other method. This layer may include the user of a per application policy enforcement point or a centralized policy authority point using user, device, and network characteristics to make a one-time and ongoing access decision.
5. Data - The data includes controls on data sharing, data classification and tagging, preventing data loss, and potentially applying data retention policy. 

[![The five zero trust elements include user, device, network, application, and data]({{site.baseurl}}/assets/playbooks/pam-zt.png)]({{site.baseurl}}/assets/playbooks/pam-zt.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 2. Define and Identify
An agency is responsible for managing the privileges of all users. To execute assigned duties, a subset of an agency’s user population may be granted elevated access. The individuals entrusted with elevated access constitute an agency’s privileged user population.

### Define a Privileged User
An agency’s privileged user population can include a range of accounts with elevated access. Given the broad-reaching nature of an organization’s privileged user population, it is important that an agency understand the user roles, groups, and accounts that constitute its privileged user population. Some common examples include:
- domain administrator
- global administrator
- application developer
- database administrator
- help desk administrator
- cybersecurity practitioner
- IT audit practitioner
- network engineer
- system administrator

{% include alert-info.html heading="Use Consistent Terms" content="Your agency may have an existing definition. The most common definition of a privileged user is a user that is authorized (and therefore, trusted) to perform security-relevant functions such as change configuration settings, run commands that require administrator access, or approve access requests." %}

Some common characteristics of a privileged user include:
- Access that can impact the confidentiality, integrity, or availability of an application.
- Access to alter data sets or multiple data sets.
- Ability to reset passwords
- Change access privileges. 
- Create accounts (especially other privileged accounts).

### Identify Privileged Accounts Across Platforms and Environments
Once a privileged user is defined, an agency can follow this process to identify its privileged users and resources.
1. Identify and document mission critical and sensitive services (most likely your high value asset list) as a starting point. Most likely, every IT system has privileged users though. Services can be further grouped by: 
- Hardware
- Operating System
- Application Type (externally accessible, internally accessible, etc.)
- Physical and logical location (data center, cloud service provider, etc.)
- Data sensitivity
2. Identify and document the IT staff roles and their associated accounts that require elevated access to perform their role. This may also include identifying a specific cyber workforce position / role required to manage the system.  
3. Perform a **Privileged Account Discovery** exercise to identify accounts that have elevated access. This can be accomplished through an automated tool or through directory analysis. Don't be surprised that there are a lot more privileged accounts than expected. The intent of privileged account discovery is to identify accounts that lack accountability. This includes group, orphaned, rogue, and default accounts which may go unnoticed or unmanaged. Discovery should include all environments including Windows, Unix/Linux, Database, Applications and cloud environments that encompass infrastructure, platform, and software as a service platforms and applications.

{% include alert-info.html heading="Why Additional Controls?" content="Most attacks start by compromising lower level accounts. Through network discovery, an attacker can find an orphaned privileged account to escalate their privileges to access applications, data, and compromise entire agency networks or data sets." %} 

The Privileged User Program should document each step either manually or automated. This step is the basis to maintain and keep accountability for an agency's privileged user population.

[![Privileged accounts can be found on Windows, Unix/Linux, Applications/Cloud, DevOps, and Machine Identities]({{site.baseurl}}/assets/playbooks/pam-identify.png)]({{site.baseurl}}/assets/playbooks/pam-identify.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 3. Integrate into ICAM
ICAM is the set of tools, policies, and systems that an agency uses to enable the right individual to access the right resources, at the right time, for the right reason in support of federal business objectives. In the context of privileged users, ICAM supports: 
- Unifying IT services by consolidating various privileged access tools at an enterprise level.
- Improving access control by tracking and monitoring privileged user accounts and access.
- Improving compliance by centralizing access requests, auditing, and reporting.

An agency should seek to leverage existing processes, controls, programs, and available tools to effectively manage its privileged user population and enterprise resources. Please refer to [Appendix D: NIST SP 800-53 Privileged User Overlay](#appendix-d-nist-sp-800-53-privileged-user-overlay) for a mapping of controls defined in SP 800-53. These controls have been augmented to serve as countermeasures for how an agency can mitigate unwanted behavior by its privileged user population.

The DHS Continuous Diagnostics and Mitigation (CDM) Program is one example of a program that provides a broad spectrum of tools that enable an agency to identify privileged user risk on an ongoing basis, prioritize these risks based on impact, and enable the agency security leadership to mitigate most significant privilege user challenges first.

### Privileged Identity Management
Identity management is how an agency collects, verifies, and manages attributes for a privileged user. An agency should only grant entitlements that the privileged user needs to perform assigned duties by leveraging segregation of duties, thus enforcing least privilege.

1. **Identify Cybersecurity Workforce Position** that outlines the appropriate responsibilities and duties. Use the [NIST Workforce Framework for Cybersecurity](https://niccs.cisa.gov/about-niccs/workforce-framework-cybersecurity-nice-framework-work-roles){:target="_blank"}{:rel="noopener noreferrer"} to identify appropriate roles.
2. **Personnel Security Vetting and Privileged User Agreement** verified by the Personnel Security Office and Privileged User Program Manager on an initial and continuing basis. The security office verifies that the existing background, suitability or fitness checks are valid and adequate. When conducting these checks, an agency should implement a consistent approach that enforces background checks that are commensurate to the privileged user’s level of risk as determined by an agency’s risk assessment (e.g. some trusted roles may require a security clearance based on their level of access). A Privileged User Agreement should also be signed by the user on a reoccurring basis. This may also be a called a rules of behavior or privileged appointment letter. This agreement highlights the responsibilities of the privileged user and acceptable rules of behavior. See [Appendix B: Privileged User Agreement for an agreement template](#appendix-b-privileged-user-agreement) An agency’s Privileged User Agreement may also include training requirements such as annual insider threat, security awareness, and tailored privileged user procedure training.
3. **Enforce Least Privileges** for a privileged user to perform their duties. If possible, implement just-in-time provisioning or implement a capability to check-out an account or password. This may also include creating custom administrator accounts scoped for the duty such as an application administrator vice a global administrator, if possible. 
4. **Manage Administrator Lifecycle** to ensure access is removed when an privileged user role changes or they are off-boarded. Accounts should be suspended or terminated within 24 hours or shorter time-frame based on security controls or risk determination.

{% include alert-info.html heading="Identity Assurance Level 3" content="Privileged users most likely require the highest level of identity proofing. The PIV identity proofing process is comparable to Identity Assurance Level 3." %} 

Training frequency is an important aspect of a privileged access management program. Privilege users should receive initial and continuing training on the following topics:
- Privilege access security principles.
- Disaster recovery and business continuity procedures.
- System characteristics and software components.

Additionally, privilege users should be notified of any changes to a system they can access.

### Privileged Credential Management
Credential management is how an agency issues, manages, and revokes privileged credentials. Agencies should user **unique, Authenticator Assurance Level 3 credentials** per each privileged user. This may include a PIV card or other two factor, cryptographic hardware authenticator identified in [NIST Special Publication 800-63-3B](https://pages.nist.gov/800-63-3/sp800-63b.html)

1. **Enforce Multi-factor Authentication (MFA)** for all administrator access. This may include a combination of factors as outlined in NIST Special Publication 800-63-3B.
2. **If used, Rotate Passwords** using a check-in/check-put capability, if possible. It is inevitable that some systems or applications must use a username and password. For those systems that do, it is a best practice to use a password vaulting tool and rotate passwords so the privileged user does not have access to the password. The password vault should be configured for Authenticator Assurance Level 3 MFA.

{% include alert-info.html heading="Authenticator Assurance Level 3" content="Privileged users most likely require the highest level of credential. A PIV card may not work in all use cases. Consider the best Authenticator Assurance Level 3 credential for each type of access." %}

For enterprise resources authenticating with Windows Active Directory, an agency may manage privilege user access with a user's PIV card. An agency may map the same PIV authentication certificate to multiple accounts using altSecurityIdentities and username hints. See the [PIV Guide section on Account Linking](https://playbooks.idmanagement.gov/piv/network/account/) for step-by-step actions to enable this feature.

For enterprise resources that do not support PIV authentication, an agency may use a privileged access gateway or management solution to enable use of a PIV card or other Authenticator Assurance Level 3 authenticators. A privileged access management tool acts as an intermediary between a privileged user and an enterprise resources such as a management console, database, or command line interface. It may provide additional capabilities such as a password vaulting, key vaulting, keystroke logging, session recording, account check-out, and just-in-time provisioning. 

### Privileged Access Management
Access management is how an agency authenticates privileged users and authorizes access to protected services.

1. **Privilege Access Request** are completed on a regular and ongoing basis. The ongoing basis activity may be called an access review or certification. This does not need to be a paper-based process and can be automated through a workflow or identity entitltement tool.
2. **Monitor Privileged User activity** via recorded sessions. Additional controls may include keyboard logging and audit log reviews (weekly or monthly) based on risk assessment. Consider user behavior automated monitoring outlined in insider threat programs. An agency can hold privileged users to a higher monitoring standard than standard users because of the heightened risk.
3. **Use a dedicated workstations** with limited applications and internet connectivity. This limits the potential risk in remote access exploitation and malware.

{% include alert-info.html heading="Preventative and Detective Measures" content="Preventative measures proactively stop inappropriate behavior through processes such as background investigations, training, rules of behavior, privileged access workstation and other mechanisms. Detective measures identify suspicious activities such as audit logs, keystroke logging, access logs, account checkout, and others. Agencies should use a combination of both to decrease privilege user risk." %}

## Step 4. Prioritize and Execute
**Get with Ross**

One of the greatest challenges in establishing any program is where to start. Step 1 identified the highest risk systems and suggested grouping systems to help identify a priority based on a number of group factors.
 
1. Windows
2. Linux/Unix
3. Applications / Web / Cloud
4. Machine Identities
5. DevOps

[Capabilities](https://www.nccoe.nist.gov/sites/default/files/library/sp1800/fs-pam-nist-sp1800-18-draft.pdf){:target="_blank"}{:rel="noopener noreferrer"}
privileged account control
privileged account command filtering (allow or deny specific commands, such as disk formatting)
multifactor authentication capability
access logging/database system
password management, including storage (vault)
separation of duties management
support least privileged policies
password obfuscation (hiding passwords from PAM users)
temporary access management
automated logging and log management (analytics, storage, alerting)
secure communications between components, where applicable
ad hoc reporting to answer management, performance, and security questions
support for multiple access levels for the PAM system (e.g., administrator, operator, viewer) protection from the introduction of new attack vectors into existing systems
a complement to, rather than the replacement of, the existing security infrastructure

# Appendix A: Reference Documentation
The following documentation references help inform the development and direction of a privilege user program.

1. [National Insider Threat Policy, November 2012](https://www.dni.gov/files/NCSC/documents/nittf/National_Insider_Threat_Policy.pdf){:target="_blank"}{:rel="noopener noreferrer"} 
   -  This policy set two priorities to strengthen the protection and safeguarding of classified information. It also references [Executive Order 13587 (October 2011)](https://www.dni.gov/files/NCSC/documents/nittf/EO_13587.pdf){:target="_blank"}{:rel="noopener noreferrer"} as the primary authority to establish insider threat programs.
      1. Created the Insider Threat Task Force.
      2. Sets the minimum standards for Executive Branch Insider Threat programs.
   
2. [National Strategy for Information Sharing and Safeguarding, December 2012](https://www.dni.gov/files/ISE/documents/DocumentLibrary/2012infosharingstrategy.pdf){:target="_blank"}{:rel="noopener noreferrer"} 
   - This strategy aims to strike the proper balance between sharing information with those who need it to keep our country safe and safeguarding it from those who would do us harm. As an agency works to extend its ICAM implementations across security domains, it is important to consider Goal #4 and PO #4 in relation to managing privileged users.
       - Goal #4 focuses on identifying, preventing, and mitigating insider threat across all domains.
       - Priority Objective #4 calls to extend and implement the FICAM roadmap across all security domains. Note: The FICAM Roadmap is superseded by the [FICAM architecture](https://playbooks.idmanagement.gov/arch/){:target="_blank"}{:rel="noopener noreferrer"} and [accompanying playbooks](https://playbooks.idmanagement.gov/){:target="_blank"}{:rel="noopener noreferrer"}.
  
3. [National Insider Threat Task Force (NITTF)](https://www.dni.gov/index.php/ncsc-how-we-work/ncsc-nittf){:target="_blank"}{:rel="noopener noreferrer"}
    - The primary mission of the NITTF is to develop a Government-wide insider threat program for deterring detecting, and mitigating insider threats, including the safeguarding of classified information from exploitation, compromise, or other unauthorized disclosure, taking into account risk levels, as well as the distinct needs, missions, and systems of individual agencies.

4. [NIST Special Publication 1800-18 - Privileged Account Management for the Financial Services Sector](https://www.nccoe.nist.gov/projects/use-cases/privileged-account-management){:target="_blank"}{:rel="noopener noreferrer"}
    - While this special publication is focused on the financial services industry it contains agnostic implementation best practices.

5. [Federal Identity, Credentials, and Access Management (FICAM) Architecture - Access Management](https://playbooks.idmanagement.gov/arch/access/){:target="_blank"}{:rel="noopener noreferrer"}
     - The FICAM Architecture is a framework for an agency to use in ICAM program and solution roadmap planning. Privileged Access Management is identified as a distinct service within the Access Management portion of the ICAM services framework.

6. [Common Sense Guide to Mitigating Insider Threats (6th Edition), February 2019](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=540644){:target="_blank"}{:rel="noopener noreferrer"}
    - The Software Engineering Institute at Carnegie Mellon University’s Insider Threat Center released the Common Sense Guide to provide the Federal Government and industry with recommendations on insider threat mitigation, based on a database of over 700 cases. This work was sponsored by the Department of Homeland Security, Office of Cybersecurity and Communications and the U.S. Secret Service. The Common Sense guide presents readers with 19 best practices to mitigate insider threats.

# Appendix B: Privileged User Agreement

Below is a template for an agency to tailor to uphold mission and business needs in support of privileged access to logical and physical resources. An agency should obtain and retain a digitally signed copy of such instruction and ensure that privileged user access to the identified protected resource is prohibited without a signed acknowledgement of system-specific rules and a signed acknowledgement of said instruction.

## [AGENCY OR PROGRAM NAME] Privileged Access User Agreement

I am being granted elevated access to [AGENCY or PROGRAM NAME] controlled systems and facilities and
am responsible for all actions taken under my accounts. I agree to the following:

1. I will only use the elevated granted to me to perform authorized tasks or mission-related
    functions.
2. I will not use my elevated access to perform routine tasks that do not require elevated
    access.
3. I will obtain and maintain required certifications and trainings according to [AGENCY OR PROGRAM
    POLICY], including but not limited to specialized role-based security or privacy training.
4. I understand the need to safeguard all credentials at the level appropriate to the data they
    protect.
5.  I will not share passwords, accounts, or other credentials with unwanted personnel.
6.  I will only add and remove users to the [ADMINISTRATOR GROUPS] group after
    receiving approval/direction from the [AGENCY OR PROGRAM POINT OF CONTACT].
7.  I will not install, modify, or remove any hardware or software without written entitlement
    and approval from the [AGENCY OR PROGRAM POINT OF CONTACT].
8.  I will not introduce any viruses, malicious/unwanted code, malware, or Trojan horse
    programs into [AGENCY OR PROGRAM NAME] systems.
9.  I will not attempt to hack the network or connected information systems, gain access to
    data or protected resources which I do not have authorized access. I will not use sensitive
    information for anything other than the purpose for which it has been authorized.
10. I understand that there are distinct information systems and access points – [AGENCY
    SECURITY DOMAINS]. I will not introduce or process data or software for information
    systems that I have not have elevated access to.
11. I will contact the [AGENCY OR PROGRAM POINT OF CONTACT] if I require clarification of my roles
    or responsibilities.

I understand that failure to comply with the above requirements may result in disciplinary action,
including termination of employment; removal or disbarment from work on federal contracts or
projects; revocation of access to federal information, information systems, and/or facilities;
criminal penalties; and/or imprisonment. I also understand that violation of certain laws, such as the Privacy Act of 1974, copyright law, and 18 USC 2071 can result in monetary fines and criminal charges that may result in imprisonment.

Printed Name:  
Date:   
Digital Signature (preferred):  

# Appendix C: Privileged Account DIRA
A Digital Identity Risk Assessment (DIRA) analyzes account privileges against what happens if the account is compromised (the risk).

**insert DIRA Example**

# Appendix D: NIST SP 800-53 Privileged User Overlay

In seeking to implement cohesive, integrated privileged user management practices an agency should consider existing controls and practices which can assist in safeguarding the enterprise’s protected resources from privileged compromise. This section provides an analysis of countermeasures for privileged user compromise by leveraging NIST SP 800- 53 security controls.

For each identified countermeasure, an accompanying explanation provides guidance on how the associated control relates to privileged users to assist an agency defend relevant protected resources. The controls are organized into the control families as listed in SP 800-53.

<table class="usa-table pam-table">
  <thead class="usa-sr">
    <tr>
      <th id="pam-table-heading-counter" scope="col">Countermeasure</th>
      <th id="pam-table-heading-control" scope="col">Control</th>
      <th id="pam-table-heading-explain" scope="col">Explanation</th>
    </tr>
  </thead>
  <tbody>
    {% for category in categories %}
      <tr class="pam-table-category-heading" data-category="{{ category }}">
        <th colspan="6" class="pam-table-heading" id="pam-table-heading-{{ category | slugify }}"><b>{{ category }}</b></th>
      </tr>
      {% for pam in site.data.overlay_pam %}
        {% if pam.category == category %}
          <tr class="pam-table-row" data-category="{{ pam.category }}">
            <td headers="pam-table-heading-{{ category | slugify }} pam-table-heading-counter">{{ pam.countermeasure }}</td>
            <td headers="pam-table-heading-{{ category | slugify }} pam-table-heading-control">{{ pam.control }}</td>
            <td headers="pam-table-heading-{{ category | slugify }} pam-table-heading-explain">{{ pam.explanation}}</td>
          </tr>
        {% endif %}
      {% endfor %} <!--pam-->
    {% endfor %}<!--category-->
  </tbody>
</table>


