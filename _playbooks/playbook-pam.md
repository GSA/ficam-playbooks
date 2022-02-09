---
layout: page
collection: playbooks
title: Privileged User Playbook
pubdate: 2022-02
type: Markdown
permalink: /playbooks/pam/
description: This Playbook provides federal agencies with best practices in managing its privileged user community.
sticky_sidenav: true
sidenav: pam

subnav:
    - text: Executive Summary
      href: '#executive-summary'
    - text: Protect Federal Identities and Logical Assets
      href: '#protect-federal-identities-and-logical-assets'
    - text: Step 1. Develop Program Goals
      href: '#step-1-develop-program-goals'
    - text: Step 2. Define and Identify
      href: '#step-2-define-and-identify'
    - text: Step 3. ICAM Integration
      href: '#step-3-icam-integration'
    - text: Step 4. Prioritize and Execute
      href: '#step-4-prioritize-and-execute'
    - text: Appendix A. Reference Documents
      href: '#appendix-a-reference-documentation'
    - text: Appendix B. Privileged User Agreement
      href: '#appendix-b-privileged-user-agreement'
    - text: Appendix C. 800-53 Privileged User Overlay
      href: '#appendix-c-nist-sp-800-53-privileged-user-overlay'
      
---

{% assign categories = "" | split: "" %}
{% for pam in site.data.overlay_pam %}
  {% assign category = pam.category | strip %}
  {% assign categories = categories | push: category | uniq | sort %}
{% endfor %}
{% assign categories = categories | uniq | sort %}
  
Version 1.0  
February 15, 2021

<a href="../../assets/img/logo-gsa.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-gsa.png" width="64" height='64' align="left" alt="U.S. General Services Administration Logo"></a>
<a href="../../assets/img/logo-cio.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-cio.png" width="64" height='64' align="left" alt="U.S. Federal Chief Information Officer Council Logo"></a>
<a href="../../assets/img/logo-cisa.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/img/logo-cisa.png" width="64" height='64' align="left" alt="U.S. Department of Homeland Security Cybersecurity and Infrastructure Security Agency Logo"></a><br><br><br>

This playbook is a collaboration between the General Services Administration Office of Government-wide Policy identity Assurance and Trusted Access Division, Federal Chief Information Security Officer Council ICAM Subcommittee, and the Department of Homeland Security (DHS) Cybersecurity and Infrastructure Security Agency (CISA) Continuous Diagnostic and Mitigation (CDM) Program.

# Executive Summary
The Privileged User Playbook is a practical guide to **help federal agencies implement and manage a Privileged User Program**. Privileged users are unique user types that perform security-related duties. A Privileged User Program enables an agency to identify, track, monitor, and audit privileged users and accounts, effectively decreasing the cyber risk impacting an agency's mission. **Unwanted behavior or compromise of privileged accounts are responsible for the most high-profile federal and private security breaches**. It is a critical Identity, Credential, and Access Management (ICAM) capability to identify privileged users and access to high value assets.

There are three prominent use cases to identify a privileged account or user.
1. Accounts used to manage IT infrastructure, resources of high value assets (HVA), and core systems such as maintenance activities on human resource applications or databases.
2. Help desk personnel with escalated privilege to perform security-relevant processes on endpoints, such as installing software on user laptops or changing endpoint configuration settings.
3. Managers that approve or recertify access or accounts.

Privileged users are managed as distinct and separate identities to decrease the risk and impact of agencies' missions.
1. These employees and contractors can jeopardize sensitive information or infrastructure, whether knowingly or unknowingly.
2. Privileged users have the potential to compromise all three core elements of information security: availability, confidentiality, and integrity.

Agencies can use this playbook to help plan and implement a logical Privileged User Program following government-wide best practices. This playbook includes a four-step process aligned with the [Federal Identity, Credential, and Access Management (FICAM) Architecture](https://playbooks.idmanagement.gov/arch/){:target="_blank"}{:rel= "noopener noreferrer"} designed for **insider threat, ICAM, and risk management professionals interested in identifying best practices for mitigating privileged user risk**. Agencies are encouraged to tailor this playbook to fit their unique organizational structure, mission, and technical requirements. Other IT program participants, including cybersecurity program managers, may value incorporating this playbook approach in their planning.

## Key Terms
These are key terms used throughout this document.
- **Account Compromise** is the unauthorized use of an account to disclosure, modify, substitute, or use sensitive information.
- **[Insider Threat](https://csrc.nist.gov/glossary/term/insider_threat){:target="_blank"}{:rel= "noopener noreferrer"}** is the potential for an insider will use their authorized access, wittingly or unwittingly, to harm the security of the United States. This threat can include damage to the United States through espionage, terrorism, unauthorized disclosure of national security information, or the loss or degradation of departmental resources or capabilities.
- **[Functional Privileged User](https://playbooks.idmanagement.gov/docs/playbook-dira.pdf){:target="_blank"}{:rel="noopener noreferrer"}** can access information resources provided by the application and approval workflows such as approving access requests.
- **[Privileged Account](https://csrc.nist.gov/glossary/term/privileged_account){:target="_blank"}{:rel="noopener noreferrer"}** is a system account used by a privileged user. A privileged account can belong to a single endpoint, domain, database, or application.
- **Privilege Compromise** is either an adverse action of a privileged user or account through an insider threat or an account compromise.
- **[Privilege Escalation](https://csrc.nist.gov/glossary/term/privilege_escalation){:target="_blank"}{:rel= "noopener noreferrer"}** is the exploitation of a bug or flaw that allows for a higher privilege level than what would usually be permitted.
- **[Privileged User](https://csrc.nist.gov/glossary/term/privileged_user){:target="_blank"}{:rel="noopener noreferrer"}** is a user that is authorized (and therefore, trusted) to perform security-relevant functions that ordinary users are not authorized to perform. Also known as a Privileged IT User, Privileged Network User or [Superuser](https://csrc.nist.gov/glossary/term/superuser){:target="_blank"}{:rel="noopener noreferrer"}.

## Disclaimer
This playbook is informative. The General Services Administration Office Government-wide Policy in collaboration with the Department of Homeland Security (DHS) Continuous Diagnostic and Mitigation (CDM) Program and the Federal CISO Council ICAM Subcommittee developed this playbook with input from federal identity and security practitioners. This playbook is limited to high-level guidance specific to privileged users accessing federal government information systems. This playbook shouldn't be interpreted as official policy or mandated action, and doesn't provide authoritative definitions for IT terms. Where appropriate, key terms from the National Institute for Standards and Technology (NIST) or Federal Information Security Management Act (FISMA) are used. This playbook supplements existing Federal IT policies and builds upon the [Office of Management and Budget Memorandum 19-17 - Enabling Mission Delivery through Improved Identity, Credential, and Access Management](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}{:rel= "noopener noreferrer"} and the [Federal Zero Trust Strategy](https://zerotrust.cyber.gov/federal-zero-trust-strategy/){:target="_blank"}{:rel= "noopener noreferrer"}, as well as existing Federal identity guidance and playbooks.

# Protect Federal Identities and Logical Assets
Government employees and contractors need elevated access to perform necessary administrative and security functions, yet this carries an inherent risk of insider threat or account compromise. As a result, agencies should implement privilege user controls that mitigate this risk without impeding their ability to carry out assigned job duties. In creating a secure physical and virtual workplace for privileged users, agencies align efforts with the [FICAM Architecture](https://playbooks.idmanagement.gov/arch/){:target="_blank"}{:rel="noopener noreferrer"}. This playbook provides informative guidance to manage federal employee and contractor privileged users by mitigating the inherent risks associated with this population. An agency achieves this outcome through the use of ICAM services. The following are the four primary steps to establish or enhance an agency's Privileged User Program.

1. [Develop Program Goals](#1-develop-program-goals) to identify the potential impact and risk to your agency's mission. Agency executives must understand why a Privileged User Program is essential and the risks associated with elevated access. This step also includes engaging agency stakeholders and government-wide groups.
2. [Define and Identify](#2-define-and-identify) a privileged user as those people and accounts that have elevated access to an agency's resources. Privileged accounts can be anywhere across a network, system, or cloud. Track and audit privileged user activity regularly.
3. [Integrate privileged users into ICAM](#3-icam-integration) for a holistic management approach. Implementing ICAM best practices and additional countermeasures to prevent privileged user and account misuse, abuse, or compromise can provide comprehensive, integrated protection of agency resources.
4. [Prioritize and Execute](#4-prioritize-and-execute) services and capabilities. Like most IT initiatives, this is a journey. Threats change, and agencies must adapt. Implementing a Privileged User Program and technology may require a multi-year project to add capabilities and services based on your agency risk and budget. The DHS CDM Program can help. An agency should leverage existing efforts to achieve information security goals by directing or tailoring playbook steps based on its resources, environment, mission, business needs, and privileged user population.

{% include alert-info.html heading= "Is this Privileged Access Management or Account Security" content=" Different vendors may use a different terms for their product. Some vendors may use the term Privileged Access or Account Management (PAM), Privileged Identity Management (PIM), Privileged Security, or something in-between. For the intent of this playbook, the agnostic privileged user is used to encompass all service areas of ICAM." %}

[![An end user account can be compromised to esclate privileges toward a domain takeover]({{site.baseurl}}/assets/playbooks/pam-journey-map.png)]({{site.baseurl}}/assets/playbooks/pam-journey-map.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 1. Develop Program Goals
Privilege compromise of an agency's privileged user population can significantly compromise an agency's mission. An agency should be fully aware of the potential risk involved in not managing a privileged user population that can lead to catastrophic events such as:
- exfiltration of sensitive or classified data;
- rendering a system inoperable through configuration changes; or
- creating and granting shadow administrator accounts for persistent access.

Privilege compromise comes in two forms:
1. Insider threat or
2. Account compromise

### Insider Threat
Insider threat is a government employee or contractor's accidental, complacent, or malicious actions. A Privileged User Program is grounded in implementing, monitoring, and reporting insider-based threats. The below table provides the definition and indicators or insider threat classifications.

| Insider Threat Classification | Definition | Example |
| --------------------- | -------------- | ------------ |
|   **Accidental**  |   Lack of awareness regarding policies, procedures, and technical competencies. | 1. Unknowingly install unapproved software.<br>2. Use privileged accounts for anything other than official administrative actions.<br>3. A privileged user accidentally deletes all data with a single command. |
|   **Complacent**  |   Overall lax or careless approach to security. | 1. Create user accounts and assign privileges without the appropriate review and approval.<br>2. Share system account passwords. |
|   **Malicious**   |  Intentionally disrupt, threaten, or endanger an organization's activities or assets. | 1. Unwanted, purposeful disclosure or theft of information.<br>2. Introduce malicious code, malware, Trojan horse, viruses.<br>3. Destroy or modify system audit logs. |

### Account Compromise
An account compromise is the unauthorized use of an account to perform an unwanted behavior. Each category of insider threat and account compromised is linked to unwanted behavior.

| Unwanted Behavior | Definition | Example |
| ----------------- | ---------- | ------- |
| **Fraud** | Unwanted use, modification, addition, or deletion of agency's data for personal gain.| On the pretense of fixing corrupt data, a database administrator modifies data without authorization.|
| **Espionage** | Sharing restricted information to aid a foreign actor or harm the U.S. Government. |  An external actor uses a compromised account to exfiltrate data.|
| **Sabotage** | Purposefully inflicting harm on an organization.| An external actor uses a phished credential to load ransomware onto a payment system. |
| **Intellectual Property Theft**| Stealing intangible assets (e.g., discoveries, inventions, designs) from an organization.| Cloud administrator uses elevated access to steal proprietary information.|
| **Unwanted Information Disclosure**| A communication or physical transfer of information to a recipient who is not authorized to access the information.| System administrator creates a "backdoor" account to access and release classified information inappropriately.|

Understanding insider threat classifications and unwanted behavior support an agency's Privileged User Program implementation. A combination of procedural and technical measures can help agencies mitigate the range of unwanted behavior. Furthermore, the relationship between the three insider threat classifications and this playbooks aids an agency in the broader effort of fulfilling the insider threat mitigation requirements in the National Insider Threat Policy and relevant Executive Orders.

### Agency Governance
A Privileged User Program is subordinate to or interacts with multiple other agency programs in most agencies.
- **High Value Asset** - [OMB Memo 19-03](https://www.whitehouse.gov/wp-content/uploads/2018/12/M-19-03.pdf){:target="_blank"}{:rel="noopener noreferrer"} outlines requirements to identify, track, and manage an agencies most critical assets. [Amplifying guidance from CISA](https://www.cisa.gov/sites/default/files/publications/Securing%20High%20Value%20Assets_Version%201.1_July%202018_508c.pdf){:target="_blank"}{:rel="noopener noreferrer"} recommended using unique accounts, logging key security events, and implementing multi-factor authentication for all HVA users, but particularly privileged users.
- **Insider Threat** - Include programs to detect and prevent the unauthorized disclosure of sensitive information. An insider threat program consists of capabilities that provide access to information; centralized information integration, analysis, and response; insider threat awareness training; and user activity monitoring on government computers.
- **Cybersecurity / ICAM** - Responsible for identity, credential, and access management services and coordination.
- **Continuous Diagnostic and Migration (CDM)** - Cybersecurity tools, integration services, and dashboards to help an agency reduce the attack surface, increase visibility into cybersecurity posture, improve response, and streamline FISMA reporting.
- **Risk Management** - Identify and track implementation and operation of security controls.

A Privileged User Program should encompass all privileged users within a Chief Information Officer's responsibility including enterprise and mission applications.

{% include alert-info.html heading= "Insider Threat Mitigation" content= "Because of privileged users' elevated access, unwanted behavior by these individuals can significantly compromise agency assets or operations. As a result, privileged user management is a cornerstone of insider threat mitigation." %}

### Program Objectives
Even though agency missions may differ, the objectives of a Privileged User Program are relatively similar. The below strategic and tactical objectives are used as a starting point to plan a Privileged User Program.

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
4. Enforce least privilege by limiting overall functions and those performed remotely.
5. Ensure privileged user activity is logged and regularly audited.

{% include alert-info.html heading= "A privileged user can be either a person and non-person" content= "It is easy to overlook the impact of device and communication channel compromise. Consider objectives for both privileged people users, and non-person entities sometimes referred to as machine identities." %}

[![Consider both person and non-person privelged users and access to protected resources.]({{site.baseurl}}/assets/playbooks/pam-iceberg.png)]({{site.baseurl}}/assets/playbooks/pam-iceberg.png){:target="_blank"}{:rel="noopener noreferrer"}

In addition to setting minimum program objectives, an agency should evaluate the risk of all users to its resources by conducting a [Digital Identity Risk Assessment (DIRA)]({{site.baseurl}}/playbooks/dira){:target= "_blank"}. The DIRA process identifies the risk of user transactions and identifies a minimum identity assurance, authenticator assurance, and federation assurance level outlined in [NIST Special Publication 800-63-3](https://pages.nist.gov/800-63-3/sp800-63-3.html){:target= "_blank"}{:rel= "noopener noreferrer"}.

### Zero Trust Alignment
NIST Special Publication 800-207 outlines a Zero Trust Architecture that moves defenses from static, network-based perimeters to focus on users, devices, network, application, and data. It shifts the operating model toward dynamic trust decisions (e.g., if a user is on an agency network and a government-furnished device, they are trusted). Within the context of this playbook, step 4 provides recommendations on how to align Privileged User Program technical measures with a zero trust architecture.

## Step 2. Define and Identify
An agency is responsible for managing all user privileges. A subset of an agency's user population may be granted elevated access to execute assigned duties. The individuals entrusted with elevated access constitute an agency's privileged user population.

### Define a Privileged User
An agency's privileged user population can include a range of accounts with elevated access. Given the broad-reaching nature of an organization's privileged user population, an agency must understand the user roles, groups, and accounts that constitute its privileged user population. Some common examples include:
- domain administrator
- global administrator
- Linux/Unix Root
- Oracle SYS
- Cisco Enable
- Windows service accounts
- SSH keys
- Emergency or break-glass accounts

{% include alert-info.html heading="Use Consistent Terms" content="Your agency may have an existing definition. The most common definition of a privileged user is a user that is authorized (and therefore, trusted) to perform security-relevant functions such as change configuration settings, run commands that require administrator access, or approve access requests." %}

Some common characteristics of a privileged user include:
- Access that can impact the confidentiality, integrity, or availability of an application.
- Access to alter data sets or multiple data sets.
- Ability to reset passwords
- Change access privileges. 
- Create accounts (especially other privileged accounts).

### Identify Privileged Accounts Across Platforms and Environments
Once a privileged user is defined, an agency can follow this process to identify its privileged users and resources.
1. Identify and document mission-critical and sensitive services (most likely your high value asset list) as a starting point. Every IT system has privileged users. Services can be further grouped by: 
- Hardware
- Operating System
- Access Type (externally accessible, internally accessible, or others)
- Physical and logical location (on-premises, cloud service provider, or others)
- Data sensitivity
2. Identify and document the IT staff roles and associated accounts requiring elevated access to perform their role. This may also include identifying a specific cyber workforce position/role required to manage the system.  
3. Perform a **Privileged Account Discovery** exercise to identify accounts that have elevated access. Accomplish this through an automated tool or directory analysis. Don't be surprised that there are many more privileged accounts than expected. Privileged account discovery intends to identify accounts that lack accountability. This includes group, orphaned, rogue, and default accounts that may go unnoticed or unmanaged. Discovery should consist of all environments, including Windows, Unix/Linux, database, applications, and cloud environments that encompass infrastructure, platform, and software as a service platforms and applications.

{% include alert-info.html heading= "Why Additional Controls?" content= "Most attacks start by compromising lower-level accounts. Through network discovery, an attacker can find an orphaned privileged account to escalate their privileges to access applications, data, and compromise entire agency networks or data sets." %} 

The Privileged User Program should document each step either manually or automated. This step is the basis to maintain and keep accountability for an agency's privileged user population.

[![Privileged accounts can be found on Windows, Unix/Linux, Applications/Cloud, DevOps, and Machine Identities]({{site.baseurl}}/assets/playbooks/pam-identify.png)]({{site.baseurl}}/assets/playbooks/pam-identify.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 3. ICAM Integration
ICAM is the set of tools, policies, and systems that an agency uses to enable the right individual to access the right resources, at the right time, for the right reason in support of federal business objectives. In the context of privileged users, ICAM supports: 
- Unifying IT services by consolidating various privileged access tools at an enterprise level.
- Improving access control by tracking and monitoring privileged user accounts and access.
- Improving compliance by centralizing access requests, auditing, and reporting.

An agency should seek to leverage existing processes, controls, programs, and available tools to effectively manage its privileged user population and enterprise resources. Please refer to [Appendix D: NIST SP 800-53 Privileged User Overlay](#appendix-d-nist-sp-800-53-privileged-user-overlay) for a mapping of controls defined in SP 800-53. These controls are augmented to serve as countermeasures for how an agency can mitigate unwanted behavior by its privileged user population.

The DHS Continuous Diagnostics and Mitigation (CDM) Program provides a broad spectrum of tools that enable an agency to identify privileged user risk on an ongoing basis. It can also help prioritize these risks based on impact and enable the agency security leadership to mitigate the most significant privilege user challenges.

### Privileged Identity Management

Identity management is how an agency collects, verifies, and manages attributes and entitlements for a privileged user. An agency should only grant entitlements that the privileged user needs to perform assigned duties by leveraging segregation of duties, thus enforcing least privilege.

1. **Identify Cybersecurity Workforce Position** that outlines the appropriate responsibilities and duties. Use the [NIST Workforce Framework for Cybersecurity](https://niccs.cisa.gov/about-niccs/workforce-framework-cybersecurity-nice-framework-work-roles){:target="_blank"}{:rel="noopener noreferrer"} to identify appropriate roles.
2. **Personnel Security Vetting and Privileged User Agreement** are completely verified by the Personnel Security Office and Privileged User Program Manager on an initial and continuing basis. The security office verifies that the existing background, suitability, or fitness checks are valid and adequate. When conducting these checks, an agency should implement a consistent approach that enforces background checks commensurate to the privileged user's level of risk as determined by an agency's risk assessment (e.g., some trusted roles may require a security clearance on their position of trust). The user should also sign a Privileged User Agreement on a reoccurring basis. This agreement may also be called a Rules of Behavior or privileged appointment letter. This agreement highlights the responsibilities of the privileged user and acceptable rules of behavior. See [Appendix B: Privileged User Agreement for an agreement template](#appendix-b-privileged-user-agreement) 
3. **Conduct Periodic Training** to ensure privileged users know their responsibilities and systems. An agency's Privileged User Agreement may also include training requirements such as annual insider threat, security awareness, and tailored privileged user procedure training. Privilege users should receive initial and continuing training on the following topics:
   1. Privilege access security principles.
   2. Disaster recovery and business continuity procedures.
   3. Current and pending architecture changes, system characteristics, and hardware and software components.
4. **Enforce Least Privileges** to only allow access to what is needed to perform their duty. If possible, implement just-in-time provisioning or implement a capability to check out an account or password. This may also include creating custom administrator accounts scoped for the duty, such as an application administrator vice a global administrator. 
5. **Manage Administrator Lifecycle** Implement and follow lifecycle management practices:
   1. Provision access when needed.
   2. Conduct access reviews every thirty days or less based on a risk determination. Modify privileges as needed. 
   3. De-provision users within 24 hours or less when access is no longer needed, their role changes, or the user leaves the organization.

{% include alert-info.html heading= "Identity Assurance Level 3" content= "Privileged users most likely require the highest level of identity proofing. The PIV identity proofing process is comparable to Identity Assurance Level 3." %} 

### Privileged Credential Management

Credential management is how an agency issues, manages, and revokes privileged credentials. Agencies should issue **unique, Authenticator Assurance Level 3 credentials** per each privileged user. This may include a PIV card or other two factor cryptographic hardware authenticator identified in [NIST Special Publication 800-63-3B](https://pages.nist.gov/800-63-3/sp800-63b.html)

1. **Enforce Multi-factor Authentication (MFA)** for all administrator access. This may include a combination of factors as outlined in NIST Special Publication 800-63-3B.
2. **Where MFA Is Not Supported, Consider a Password Vaulting Tool** with a check-in/checkout capability. It is inevitable that some systems or applications must use a username and password. It is best to use a password vaulting tool and rotate passwords after every use. The password vault should be configured for Authenticator Assurance Level 3 access.

{% include alert-info.html heading= "Authenticator Assurance Level 3" content= "Privileged users require the highest level of credential. A PIV card may not work in all use cases. Consider the best Authenticator Assurance Level 3 credential for each type of access use case." %}

For enterprise resources authenticating with Windows Active Directory, an agency may manage privileged user access with a user's PIV card. An agency may map the same PIV authentication certificate to multiple accounts using altSecurityIdentities and username hints. See the [PIV Guide section on Account Linking](https://playbooks.idmanagement.gov/piv/network/account/) for step-by-step actions to enable this feature.

For enterprise resources that do not support PIV, an agency may use a privileged access gateway or management solution to enable a PIV card or other phishing-resistant authenticator. A privileged access management tool is an intermediary between a privileged user and an enterprise resource such as a management console, database, or command-line interface. It may provide additional capabilities such as password vaulting, key vaulting, keystroke logging, session recording, account checkout, and just-in-time provisioning. Agencies should not disable native MFA to use a password vaulting tool.

### Privileged Access Management
Access management is how an agency authenticates privileged users and authorizes access to protected services.

1. **Privilege Access Request** are completed regularly and ongoing. The ongoing basis activity may be called an access review or certification. Access reviews may be a paper-based process but make a plan to automate this process through a workflow or identity entitlement tool.
2. **Monitor Privileged User Activity** via activity logging and regular log reviews. Additional controls may include keystroke logging and session recording based on risk assessment. Consider user behavior automated monitoring outlined in insider threat programs. Because of the heightened risk, an agency can hold privileged users to a higher monitoring standard than standard users.
3. **Use Dedicated Workstations** with limited applications and internet connectivity. This limits the potential risk in remote access exploitation and malware.

{% include alert-info.html heading= "Preventative and Detective Measures" content=" Preventative measures proactively stop inappropriate behavior through processes such as background investigations, training, rules of behavior, privileged access workstation and other mechanisms. Detective measures identify suspicious activities such as audit logs, keystroke logging, access logs, and account checkout. Agencies should use a combination of both to decrease privilege user risk." %}

## Step 4. Prioritize and Execute
Understand the data flows and access types when designing a Privileged User Program technical reference architecture. The basic components of a privileged user system include:

1. Directory

<< architecture Diagram modified from DoD zero trust and microosft>>



- map privileged accounts back to a single person. Remove access to both when they move.

1. Inventory systems to focus on those that have a FIPS categorization of High for Confidentiality or Integrity (from Step 2).

2. Scan systems to discover privileged accounts that exist on those systems, update inventory in Step 2 as necessary.

3. Categorize systems by system purpose, system impact, operating system, and sensitivity.
    
    a) Use DIRA to understand the authenticator level of assurance required for the system based on system sensitivity.
    
    b) Production systems are more critical than non-production systems.
    
    c) Systems that control other systems (i.e Active Directory) are more critical than single-purpose systems.

4. Choose a champion to begin the implementation process
    
    a) Choosing an initial group of privileged users that are supportive of the process change management required is a great step in overcoming resistance to change.
    
    b) Implement incrementally, first within the champion organization and expand based on readiness.
    
    c) Learn from the each group experience to ease subsequent groups integrations.

5. Start with basic account management, ensuring that the most impactful accounts are well in control.
    
    a) Accounts should be provisioned to only authorized administrators who have committed to the responsibilities of their job
    (see Appendix B).
    
    b) Administrators should utilize PIV or other Multifactor Authentication directly where possible.
    
    c) Where not possible PIV or MFA should be required to access vaulted secrets and session monitoring should be utilized for the most sensitive accounts.

6. Advanced capabilities such as separation of duties enforcement/detection, privileged threat analytics, fine grained entitlements management, SIEM integration should be introduced as the agency matures in their PAM implementation.
    
    a) Look for specific issues that have been experienced in the agency when deploying advanced capabilities.
    
    b) SIEM integration is a great next step but requires a mature SIEM capability in order to execute.
    
    c) Use capabilities from other ICAM services, such as Identity Governance and Administration (IGA), to bring privileged users into context of the user in the organization.
    
    d) A privileged user is first a user in the environment, and when integrated IGA can ensure that privileges assigned to a user are appropriate to their current job or role         within an agency.
    
    e) Access control methods such as RBAC are complex to implement. Implementing a set of “birthright” access rules such as access to a “safe” when a person is added to a             security group to administrator a system can ease the management burden.
    
    f) The rule here should be coverage and then depth. Bring all of the sensitive accounts under control and then apply further analysis and control on those accounts.


One of the greatest challenges in establishing any program is where to start. Step 1 identified the highest risk systems and suggested grouping systems to help identify a priority based on a number of group factors.
 
1. Windows
2. Linux/Unix
3. Applications / Web / Cloud
4. Machine Identities
5. DevSecOps - One page with devops graphic Automation is the friend of DEVOPS as it enables the development process and if we are thoughtful we can use automation to build security automation into the CI/CD pipeline; I will refer to this as DEVSECOPS. Considering the development team this means applying automation across the entire software development lifecycle (SDLC) through the workflow that supports the various events, such as checking in code, in the CI/CD pipeline. Security can’t be an afterthought in your CI/CD pipeline and security must be treated as importantly as the code itself. The earlier an anomaly or defect can be prevented or found in the CI/CD pipeline, the less costly that mistake is, and automation can help us discover defects earlier. DEVSECOPS pipelines use privileged accounts which can be major targets for adversaries if not managed properly. At each of these points in the pipeline there will be a specific set of users that can perform operations, and these operations will have a specific set of privileges. The practice of managing users, accounts, privileges and access control is broadly called Identity and Access Management (IAM) and a subset of for managing privileged users is, known as privileged access management (PAM) or privileged user management (PUM) focuses on persons and systems with elevated permissions or entitlements.  In the context if DEVSECOPS we will consider developers and operators of the CD/CD pipeline as privileged and discuss components of IAM/PAM that supports this. For instance, consider the “CODE” portion of the cycle in Figure 1 where we have developers working on the code. There are likely several developers and they need to have full rights to work in their local machines including adding supporting software and tools that make their jobs easier. It is likely that they will use code repositories such as git and have access to development planning tools such as JIRA and to integrated development environments like eclipse. When performing development each of these tools have a high level of privileges, administrator access, but the process that enables the “BUILD” step will be limited to the person(s) that manage that activity. Contrast that with the “DEPLOY” portion of the cycle in Figure 1 we will see engineers that are expert in the managing of compute power (servers), networking, and production controls. They necessarily use well-considered means of moving code and services from testing environments into production in a manner that will not disturb other operating capabilities and won’t expose the organization to additional risk. Deployment engineers will likely have access to systems at administrator level and these entitlements need to ensure that separation of duties is employed. The IAM system can be configured such that separations enforce that an individual that deploys the database does not have access to change the operational data IN the database but can only manage the database itself. Finally, if we look at the “PLAN” portion of the cycle where we are going to iterate on our development, some business owner will determine the investment that should be made during the next iteration(s) and some of this information might involve projected costs that are closely held. Only the sponsor, the project manager, and the acquisition and procurement persons would have access to the protected cost information which is probably going to exist in some excel spreadsheets or some accounting and procurement system. The outcomes of this business exercise will be an approval and budgeted line of accounting which are formal mechanisms in the business governance with limited access but the artifacts that describe the expected outcomes of the development and delivery are necessarily focused on the expected outcomes of the development with only a simple communication of expected budget for the iteration(s).

Call out - DEVOPS tools have been a primary target of attackers who have been able to extract privileged account credentials in one environment (say DEV) and use them in subsequent environments (production). Solarwinds.

Call out - On the CDM Program the architecture supports managing all users in the IGA platform which is SailPoint in most cases, aggregating information about the user’s TRUST (identity and background checks), CRED (the credentials that have been issued to the individual) BEHAVE (training the person has completed) Accounts (such as from AD) and PRIV (these are the privileged accounts entitlements) that the PAM tool CyberArk or CA PAM manages. Information from these sources will be provided to SIEM, Auditing and to an organization Dashboard to enable each organization to have an enterprise view of risk associated with users. This information can further be provided as summary information to a cross-organizational dashboard to get a view of risk across the entire eco-system.

User or Device Repository – This can be Active Directory or some other LDAP store or the IGA tool itself
Identity Governance platform – Typically this consists of policy and workflow engines and stores information about users and their entitlements (both access and role). Has complete ability to audit all requests for access and the result of the workflow. IGA platforms can enable periodic certification of entitlements to ensure person still needs access they have been granted in the past.
Connectors to resources – Actions taken by the IGA platform is to provision, update or de-provision account access to the access control point of an application or service. Common connectors to databases, Active Directory, LDAP and custom connectors to systems like databases and application platforms are usually available for this purpose.
Privileged Access Manager – Typically this is a policy and workflow engine that is dedicated to managing privileged user access.
Privileged Vault – A store of secrets that is used by the PAM solution to enable access to the target devices or applications.

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

4. [OMB Memo 17-09 - Management of Federal High Value Assets](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2017/m-17-09.pdf){:target="_blank"}{:rel="noopener noreferrer"}
    - General guidance for the planning, identification, categorization, prioritization, reporting, assessment, and remediation of Federal High Value Assets (HV As).

5. [NIST Special Publication 1800-18 - Privileged Account Management for the Financial Services Sector](https://www.nccoe.nist.gov/projects/use-cases/privileged-account-management){:target="_blank"}{:rel="noopener noreferrer"}
    - While this special publication is focused on the financial services industry it contains agnostic implementation best practices.

6. [NIST Interagency Report 7966 - Security of Interactive and Automated Access Management Using Secure Shell (SSH)](https://csrc.nist.gov/publications/detail/nistir/7966/final){:target="_blank"}{:rel="noopener noreferrer"}
  - This publication assists organizations in understanding the basics of SSH interactive and automated access management in an enterprise, focusing on the management of SSH user keys.

7. [Federal Identity, Credentials, and Access Management (FICAM) Architecture - Access Management](https://playbooks.idmanagement.gov/arch/access/){:target="_blank"}{:rel="noopener noreferrer"}
     - The FICAM Architecture is a framework for an agency to use in ICAM program and solution roadmap planning. Privileged Access Management is identified as a distinct service within the Access Management portion of the ICAM services framework.

8. [Common Sense Guide to Mitigating Insider Threats (6th Edition), February 2019](https://resources.sei.cmu.edu/library/asset-view.cfm?assetid=540644){:target="_blank"}{:rel="noopener noreferrer"}
    - The Software Engineering Institute at Carnegie Mellon University’s Insider Threat Center released the Common Sense Guide to provide the Federal Government and industry with recommendations on insider threat mitigation, based on a database of over 700 cases. This work was sponsored by the Department of Homeland Security, Office of Cybersecurity and Communications and the U.S. Secret Service. The Common Sense guide presents readers with 19 best practices to mitigate insider threats.

# Appendix B: Privileged User Agreement

An agency can tailor [this template](../../docs/template-pua.docx){:target="_blank"} to uphold mission and business needs in support of privileged user access to logical and physical resources. An agency should obtain and retain a digitally signed copy of such instruction and ensure that privileged user access to the identified protected resource is prohibited without a signed acknowledgement of system-specific rules and a signed acknowledgement of said instruction.

## [AGENCY OR PROGRAM NAME] Privileged User Agreement

Version 1.0  
Last Updated: August 10, 2021

I am being granted elevated access to [AGENCY or PROGRAM NAME] controlled systems and facilities and am responsible for all actions taken under my accounts. I agree to the following:

1.	I will only use my elevated privileges to perform authorized tasks or mission-related functions on systems I am authorized to access.
2.	I will not use my elevated privileges to perform routine tasks that do not require elevated access.
3.	I will obtain and maintain required certifications and trainings according to [AGENCY OR PROGRAM POLICY], including but not limited to specialized role-based security and privacy training.
4.	I understand the need to safeguard all credentials at the level appropriate to the data they protect.
5.	I will not share passwords, accounts, or other credentials with unwanted personnel.
6.	I will only add and remove users to the [ADMINISTRATOR GROUPS] group after receiving approval/direction from the [AGENCY OR PROGRAM POINT OF CONTACT].
7.	I will not install, modify, or remove any hardware or software without written approval from the [AGENCY OR PROGRAM POINT OF CONTACT].
8.	I will not knowingly introduce any viruses, malicious/unwanted code, malware, or Trojan horse programs into [AGENCY OR PROGRAM NAME] systems.
9.	I will not attempt to hack the network or connected information systems, gain access to data or agency assets which I am authorized to access. I will not use sensitive information for anything other than the purpose for which it has been authorized.
10.	I will contact the [AGENCY OR PROGRAM POINT OF CONTACT] if I require clarification of my roles or responsibilities.

I understand that failure to comply with the above requirements may result in disciplinary action, including termination of employment; removal or disbarment from work on federal contracts or projects; revocation of access to federal information, information systems, and/or facilities; criminal penalties; and/or imprisonment. I also understand that violation of certain laws, such as the Privacy Act of 1974, copyright law, and 18 USC 2071 can result in monetary fines and criminal charges that may result in imprisonment.

Printed Name:  
Date:   
Digital Signature (preferred):  

# Appendix C: NIST SP 800-53 Privileged User Overlay

In seeking to implement cohesive, integrated privileged user practices an agency should consider existing controls and practices which can assist in safeguarding the enterprise’s protected resources from privileged compromise. This section provides an analysis of countermeasures for privileged user compromise by leveraging NIST SP 800- 53 security controls.

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


