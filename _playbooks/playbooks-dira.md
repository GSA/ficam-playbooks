---
layout: page
collections: playbooks
navtitle: Digital Identity Risk Assessment Playbook
title: Digital Identity Risk Assessment Playbook
pubdate: 09/2020
date: September, 13, 2021
type: Markdown
permalink: /playbooks/dira/
description: The Digital Identity Risk Assessment playbook is a six-step playbook for completing a digital identity risk assessment as described in OMB Memo 19-17 and NIST Special Publication 800-63-3.
sticky_sidenav: true
sidenav: dira

subnav:
  - text: Introduction
    href: '#introduction'
  - text: High-Level DIRA Process
    href: '#high-level-dira-process'
  - text: Step 1. Identify Users, Transactions, and Roles
    href: '#step-1-identify-users-transactions-and-roles'
  - text: Step 2. Identify Risks and Assurance Levels
    href: '#step-2-identify-risks-and-assurance-levels'
  - text: Step 3. Determine Steps to Meet Assurance Levels
    href: '#step-3-determine-steps-to-meet-assurance-levels'
  - text: Step 4. Finalize Digital Identity Acceptance Statement
    href: '#step-4-finalize-digital-identity-acceptance-statement'
  - text: Step 5. Reassess
    href: '#step-5-reassess'
  - text: Agency Process Plays
    href: '#agency-process-plays'
  - text: Play 1. Streamline Risk Management and Assessment Processes
    href: '#play-1-streamline-risk-management-and-assessment-processes'
  - text: Play 2. Add Context for the Mission
    href: '#play-2-add-context-for-the-mission'
  - text: Play 3. Use Templates
    href: '#play-3-use-templates'
  - text: Play 4. Shortcut Decision Trees
    href: '#play-4-shortcut-decision-trees'
  - text: Play 5. Leverage Existing Agency Tools
    href: '#play-5-leverage-existing-agency-tools'
  - text: Play 6. Less Is More
    href: '#play-6-less-is-more'
  - text: Policy, Standards, and Guidance
    href: '#policy-standards-and-guidance'
  - text: NIST Special Publication 800-63-3 Requirements Traceability Matrix
    href: '#nist-special-publication-800-63-3-requirements-traceability-matrix'
  - text: NIST Special Publication 800-63 Updates
    href: '#nist-sp-800-63-updates'
---

This playbook reflects the contributions of the Digital Identity Risk Assessment working group of the Identity, Credential and Access Management Subcommittee (ICAMSC).  The working group was co-chaired by members from the Internal Revenue Service (IRS) and the Environmental Protection Agency (EPA). Contributions were made by the members of services or agencies representing the Center of Medicare and Medicaid Services (CMS), Department of Defense (DOD), Department of Health and Human Services (HHS), Department of Homeland Security (DHS), Department of Justice (DOJ), Department of the Treasury (USDT), Department of Transportation (DOT), and General Services Administration (GSA). 

# Introduction

Digital identity represents each individual engaged in an online transaction. However, an individual’s real-life identity may not be known when used to access a digital service (a digital service is any federal Information Technology (IT) system or application accessible over the public internet or agency intranet). Identity proofing helps establish that the individual is who they claim to be. Digital authentication provides reasonable risk-based assurances that the individual accessing the application is the same individual who previously accessed the service.  This playbook is a method to apply the National Institute of Standards and Technology (NIST) Special Publication 800-63-3: Digital Identity Guidelines.  Federal agencies can perform a Digital Identity Risk Assessment (DIRA) to determine the appropriate identity, authenticator, or federation level outlined to access an application. A DIRA is a method of applying Digital Identity Risk Management required by OMB Memorandum 19-17: Enabling Mission Delivery through Improved Identity, Credential, and Access Management, and NIST Special Publication 800-63-3 Digital Identity Guidelines.

## Purpose

Most federal agencies offer services through an IT system or application, such as a website, to their employees, other agencies, and the public. To access an application, users may need to provide identity information, create an account, and log in. These actions are part of the digital identity and authentication process. 

DIRAs determine the assurance levels for the digital transactions that involve digital identity or require human authentication.  When agencies build or buy applications that use the most current identity proofing and authentication standards, they protect both the digital transactions and the user and agency data behind the applications.

This Digital Identity Risk Assessment playbook helps federal agency Chief Information Officer (CIO) and Chief Information Security Officer (CISO) teams and business application owners to:

-	Update and maintain consistent processes;
-	Determine whether an agency application requires a DIRA;
-	Integrate DIRA into agency Risk Management Framework (RMF) processes; and
-	Learn practices to implement DIRA processes.

NIST publishes implementation guides (for more information, refer to [NIST Special Publication 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3){:target="_blank"}{:rel="noopener noreferrer"}) and frequently asked questions (FAQs) (NIST Special Publication 800-63-3: Digital Identity Guidelines, Frequently Asked Questions)  for agencies and service providers to use to create information technology solutions to meet these standards. This playbook promotes consistency, effectiveness, and efficiency in your agency’s processes.

## How to Use This Playbook

This playbook is divided into three major sections. Read the entire playbook or jump directly to the section that will help your agency.
- [High-Level DIRA Process](#high-level-dira-process) - A step-by-step guide on how to approach a DIRA process for each agency.
- [Agency Process Plays](#agency-process-plays) - Six plays to create efficient and consistent processes. For example, Play #4 includes a shortcut decision tree for a streamlined DIRA for some applications.
- [NIST SP 800-63 Updates](#nist-sp-800-63-updates) - Information about updates to NIST Special Publication 800-63. 

## Scope

The DIRA playbook applies to all federal Information Technology (IT) systems and applications that need identity proofing and authentication (pursuant to 0MB Circular A-130, "information system" means a discrete set of information resources organized for the collection, processing, maintenance, use, sharing, dissemination, or disposition of information. *System* and *application* are used synonymously throughout this playbook). This playbook complements the following standard and policy:

- [NIST Special Publication 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3){:target="_blank"}{:rel="noopener noreferrer"}
- [Office of Management and Budget Memorandum (OMB) M-19-17: Enabling Mission Delivery through Improved Identity, Credential, and Access Management](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}{:rel="noopener noreferrer"}

All agency information technology systems should use the DIRA process as part of the Risk Management Framework (RMF) and Federal Information Security Modernization Act (FISMA) processes. Business owners and information security officers produce a Digital Identity Assessment Statement (DIAS) to document the assurance levels determined by collecting and analyzing the system or application data as part of the assessment process.

This playbook does not apply to:

-	Non-person entities (refer to NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 2.3: A Few Limitations), such as devices, Robotic Process Automation (RPA) or Machine Learning;
- Facilities access;
- Federation Assurance Level 3 solutions (working group members determined that Federation Assurance Level 3 was complex and not widely supported in commercial products and implementations; the working group decided the Federation Assurance Level 3 explanations were better served by agency technical exchanges or deferred to details included in NIST Special Publications); or
- National security systems (NSS) (refer to Federal Information Security Modernization Act of 2014, 44 U.S.C. § 3551 et seq., Public Law (P.L.) 113-283, December 8, 2014).

# High-Level DIRA Process

The DIRA process begins when a new application or system is identified or a time-driven or event-driven reassessment is triggered. Once it is determined that a DIRA is needed, application data is identified, collected, and analyzed to determine the assurance levels, and produce a Digital Identity Assessment Statement (DIAS), as shown in Figure 1.

[![This is a circle figure with five steps. The DIRA process starts at the top of the circle when a new application or system is identified or when a time or event-based reassessment is triggered. Step 1 is Identify User, Transactions, and Roles. Step 2 is Identify Risks and Assurance Levels. Step 3 is Determine Steps to Meet Assurance Levels. Step 4 is Finalize Digital Identify  Assessment Statement. Step 5 is Reassess. Return back to Step 1 based on new application or event trigger.]({{site.baseurl}}/assets/playbooks/DIRAFigure1.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure1.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 1: Example DIRA Process</b></p>

A high-level DIRA process includes five steps:
1)	Identify Users, Transactions, and Roles
2)	Identify Risks and Assurance Levels
3)	Determine Steps to Meet Assurance Levels
4)	Finalize Digital Identity Assessment Statement
5)	Reassess

## Step 1. Identify Users, Transactions, and Roles 

The first step is to identify the users and transaction information as well as the functional and business roles of the application.
There are many definitions to categorize users within the federal government, such as:  
-	User Types - Organizational and Non-Organizational users
-	Communities of Users - Employee, Partner, and Public users
-	Common Roles - General, Functional Privileged, and IT Privileged users

These definitions simplify complex requirements related to individuals and privacy, information security, and identity and access management concepts.  

{% include alert-info.html heading="Key Point" content="Identifying categories of users helps define the requirements for more than the Digital Identity Risk Assessments. For example, requirements for privacy, records retention, and monitoring are based on user types and categories." %}

First, identify the user types and communities of users the application supports. Identifying an application’s community of users is important to the DIRA processes as communities have different privacy, regulatory, and solution requirements to consider in risk assessments. Table 1 identifies user types and five common examples of communities of users. 

**Table 1: Examples of User Types and Communities**

| User Type | Description | Examples of Community of Users |
| ----------- | ------------ | ---------------------------------- |
| Organizational | An employee or individual the organization deems to have equivalent status of an employee | Internal agency enterprise users, including employees and direct support contractors <br><br>Other federal government agency users |
| Non-organizational | All users other than organizational users (i.e., the general public or guests) | U.S. state, local, and tribal agency users<br><br>Non-profit, business, or commercial users<br><br>Public or other users |

Next, identify each transaction the communities of users can perform in the application. 
Per NIST Special Publication 800-63-3: Digital Identity Guidelines, Appendix A, Definitions and Abbreviations, a transaction  is “... a discrete event between a user and a system that supports a business or programmatic purpose. A government digital system may have multiple categories or types of transactions, which may require separate analysis within the overall digital identity risk assessment.” 

Application owners and the information security team collaborate to identify, analyze, and assess the digital transactions of the application. Examples of transactions and transaction types are phrased as actions on data: Create, Read, Modify, Delete. 

{% include alert-info.html heading="Key Point" content="Summarize transactions by each community of users for risk assessments. Each transaction carries a unique set of risks depending on the type of data being accessed and what the user can do with the data." %}

Finally, map the community of users to the common roles. Most applications have several different user roles, each with different access privileges. Examples of common user roles include:
-	**General users**
    - Can access: Information resources provided by the application
    - Examples: Employees, general public
-	**Functional privileged users**
    -	Can access: Information resources provided by the application, and approval workflows
    -	Examples: Managers
-	**Information Technology (IT) privileged users**
    -	Can access: IT systems with read, write, or change access
    -	Examples: System administrators, security analysts

Table 2 provides examples of user types, transactions, and roles. 

**Table 2: Examples of User Types and Transactions**

| User Type | Community of Users | Example |
| ----------- | ------------ | ---------------------------------- |
| Organizational | Other federal government agency user | Agency employee or contractor (User Type) accesses and uploads document to cross-agency collaboration platform (Transaction) |
| Organizational | Internal agency enterprise user | Agency employee administrator (Role) adds user to an agency’s collaboration platform (Transaction) |
| Organizational | Internal agency enterprise user | Agency employee or contractor (User Type) exports data for use outside of the system (Transaction) |
| Organizational | Internal agency enterprise user | Agency employee supervisor (Role) approves a pending payment (Transaction) |
| Organizational | Internal agency enterprise user | Agency employee supervisor (Role) processes a payment (Transaction) |
| Non-organizational | Public user | Public user (User Type) searches for national park information and resources (Transaction) |
| Non-organizational | Public user | Public user (User Type) applies for federal government employment (Transaction)|
| Non-organizational | Public user | Public user (User Type) retrieves tax information (personally identifiable information [PII]) (Transaction)|

## Step 2. Identify Risks and Assurance Levels 

Determine the digital identity risk for each assurance category by assessing the impacts for each community of user, user type, common role, and transactions identified in Step 1.  

-	**Identity Assurance Levels (IALs)** indicate the level of confidence in a claimed identity. 
-	**Authenticator Assurance Levels (AALs)** indicate authentication requirements.
-	**Federation Assurance Levels (FALs)** indicate the level of confidence in an assertion used to communicate identity or authentication information across applications or across agencies. 

The risks and impact assessment considers the risks to both the agency and the user for the transactions. The risk to one can be significant while not negatively impacting the other at all. It’s common for government applications to have different assurance levels based on differing impacts and risks for each community of users and transactions.

{% include alert-info.html heading="Key Point" content="The impact categories and definitions used in the DIRA process are the same used to determine the overall application system categorization for impacts to confidentiality, integrity, and availability (a FIPS 199 assessment).<br><br>However, your overall application system categorization (FIPS 199) is often different than the risks and impacts for the identity and authenticator assurance levels for communities of users and transactions for the DIRA." %}

Table 3 lists the six impact categories to use. This table is a guideline for categorizing the risks and impacts involved in your application users and transactions.

**Table 3: Impact Definitions**

| Impact Category | Low | Moderate | High |
| ----------- | ------------------- | ------------------------ | --------------------- |
| **Inconvenience, distress, or damage to standing or reputation** | At worst, limited, short-term inconvenience, distress, or embarrassment to any party. | At worst, serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party. | Severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals. |
| **Financial loss or agency liability** | At worst, an insignificant or inconsequential financial loss to any party or an insignificant or inconsequential agency liability. | At worst, a serious financial loss to any party or a serious agency liability. | Severe or catastrophic financial loss to any party, or severe or catastrophic agency liability.|
| **Harm to agency programs or public interests** | At worst, a limited adverse effect on organizational operations or assets, or public interests. Examples of limited adverse effects are: (i) mission capability degradation to the extent and duration that the organization is able to perform its primary functions with noticeably reduced effectiveness, or (ii) minor damage to organizational assets or public interests. | At worst, a serious adverse effect on organizational operations or assets, or public interests. Examples of serious adverse effects are: (i) significant mission capability degradation to the extent and duration that the organization is able to perform its primary functions with significantly reduced effectiveness, or (ii) significant damage to organizational assets or public interests.| A severe or catastrophic adverse effect on organizational operations or assets, or public interests. Examples of severe or catastrophic effects are: (i) severe mission capability degradation or loss of to the extent and duration that the organization is unable to perform one or more of its primary functions, or (ii) major damage to organizational assets or public interests. |
| **Unauthorized release of sensitive information** | At worst, a limited release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in a loss of confidentiality with a low impact as defined in FIPS 199. | At worst, a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a moderate impact as defined in FIPS 199. | A release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a high impact as defined in FIPS 199. |
| **Personal safety** | At worst, minor injury not requiring medical treatment. | At worst, moderate risk of minor injury or limited risk of injury requiring medical treatment. | A risk of serious injury or death. |
| **Civil or criminal violations** | At worst, a risk of civil or criminal violations of a nature that would not ordinarily be subject to enforcement efforts. | At worst, a risk of civil or criminal violations that may be subject to enforcement efforts.| A risk of civil or criminal violations that are of special importance to enforcement programs. |

### Identity Assurance

Identity Assurance Levels define the processes and solutions used to identity proof users attempting to sign up for a digital service or perform an application transaction. IALs mitigate impacts of providing a benefit or information to the wrong user. 
-	Identity Assurance is: “Are you who you say you are?”
-	Impacts are: “What are the risks to the government or to you if you aren’t?”
	
Defining the IALs for each community of users and transactions from Step 1 is one of the more challenging aspects of a DIRA. The final IAL correlates to how much personal data (personal data is Personally Identifiable Information [PII]. As defined by OMB Circular A-130, PII is information that can be used to distinguish or trace an individual’s identity, either alone or when combined with other information that is linked or linkable to a specific individual) is validated and verified for that user during the identity proofing process. Agencies collecting identity information as part of identity proofing may be subject to specific retention policies in accordance with applicable laws, regulations, or policies, including any National Archives and Records Administration (NARA) records retention schedules. 

At Identity Assurance Level 1 (IAL1), the application may or may not require proofing. If an application requires input, a user may only need to provide a real or fictitious name for display purposes and an email address to receive notifications. The information may be self-asserted by the user and doesn’t need to be verified. At Identity Assurance Level 2 (IAL2) or 3 (IAL3), increasingly more personal information about the user needs to be validated and verified either remotely, supervised remotely, or in person. At IAL2, a real name, an email address, and an address of record are confirmed through record checks remotely or in person. At IAL3, a biometric is captured and the user must be verified in person.

{% include alert-info.html heading="Key Point" content="The risks and impacts of excessive information collection for identity proofing needs to be strongly considered for each community of users and the transactions.<br><br>For public users and other non-organizational users, privacy benefits and privacy principles are key factors to consider.<br><br>Application owners and agency processes need to include the Senior Agency Official for Privacy to define the risks, impact levels, and the Identity Assurance Levels 
." %}

Figure 2 explains the three Identity Assurance Levels in example terms of the information validated and verified during the identity proofing process. Refer to NIST Special Publication 800-63-3A: Digital Identity Guidelines, Enrollment and Identity Proofing, Section 4, Identity Assurance Level Requirements (page 5) for the detailed requirements of the identity proofing processes.

[![Figure 2 is a building block figure. A user is on the right of the figure and to the left of the user are different data elements provided by a user. Each IAL includes addition data to increase the assurance. IAL 1 data includes Display Name & Email Address. IAL 2 data includes confirmed through record checks through virtual or in-person, address of record, and real name & email address. IAL 3 data includes confirmed through record checks and in-person, biometric, address of record, and real name & email address.]({{site.baseurl}}/assets/playbooks/DIRAFigure2.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure2.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 2: Identity Assurance Levels</b></p>

Figure 3 is an example of a decision tree of the risk assessment process flow that defines the Identity Assurance Levels for the communities of users and transactions in Step 1. Additional decision trees are in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels.

[![Figure 3 is a decision tree to select an appropriate Identity Assurance Level (IAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, do you need any Personally Identifiable Information (PII) or Protected health information (PHI)? If no, select IAL1. If yes, do you need the PII/PHI to be validated? If no, select IAL1. If yes or if you don’t know, specify the risks (to the agency or the subject) of providing the digital service (i.e., a person falsely claiming an identity) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select IAL3. If no, did you assess moderate for personal safety? If yes, select IAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select IAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select IAL2. If no, are you making personal data accessible? If yes, select IAL2. If no, select IAL1. Reassess the IAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.]({{site.baseurl}}/assets/playbooks/DIRAFigure3.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure3.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 3: Identity Assurance Level Decision Tree</b></p>

### Authenticator Assurance

Authenticator Assurance Levels define the strength of the authentication process. AALs mitigate potential authentication errors (i.e., an attacker accessing a user’s account).
-	Authenticator Assurance is: “Is this the same user as before?”
-	Impacts are: “What are the risks to the government or to you if you are not the same user as before?”

At Authenticator Assurance Level 1 (AAL1), a user might only use a username and password. At Authenticator Assurance Level 2 (AAL2), a user has two factors, including a factor such as a one-time password (OTP) managed by a mobile application on a personal or government mobile phone (refer to NIST Special Publication 800-63-3B: Digital Identity Guidelines, Authentication and Lifecycle Management, Section 4, Authenticator Assurance Level requirements). 

{% include alert-info.html heading="Key Point" content="Two-factor authentication is rapidly becoming the expected default for applications.<br><br>Recurring public and other non-organizational users may want to create an account. Agencies and application owners should strongly consider always allowing and providing two-factor options.<br><br>For employees and other organizational government users, two-factor authentication is a government-wide policy requirement." %}

Figure 4 explains the concept of the three Authenticator Assurance Levels in example terms of the authentication (refer to NIST Special Publication 800-63-3B: Digital Identity Guidelines, Authentication and Lifecycle Management, Section 4, Authenticator Assurance Level requirements).

[![This figure is a building block figure. A user is on the right of the figure and to the left of the user are different authenticator elements used to log in. Each AAL includes an authentication factor to increase the assurance. AAL 1 includes a single factor. AAL 2 includes two factors. AAL 3 includes two factor with cryptographic hardware.]({{site.baseurl}}/assets/playbooks/DIRAFigure4.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure4.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 4: Authenticator Assurance Levels</b></p>

Figure 5 is an example of the risk assessment process flow that defines the Authenticator Assurance Levels for the community of users and transactions in Step 1. Additional decision trees can be found in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels. The decision tree in Figure 5 is another example used by federal agencies.

[![Figure 5 is a decision tree to select an appropriate Authenticator Assurance Level (AAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, specify the risks (to the agency or the subject) of providing the digital service (i.e., a false claimant using an identity that is not theirs) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select AAL3. If no, did you assess moderate for personal safety? If yes, select AAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select AAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select AAL2. If no, are you making personal data accessible? If yes, select AAL2. If no, select AAL1. Reassess the AAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.]({{site.baseurl}}/assets/playbooks/DIRAFigure5.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure5.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 5: Authenticator Assurance Level Decision Tree</b></p>

### Federation Assurance

Federation Assurance Levels (FALs) indicate the assertion protocol used by an application to communicate identity and authenticator information. FALs protect information about the authenticated user. They mitigate risks if a malicious actor in the transaction changes or replays the information. 

{% include alert-info.html heading="Key Point" content="Federation is an advanced topic with many different acronyms and terms.<br><br>Use outcome-based examples and demonstrations with application owners and business teams to help identify the FALs." %}

This playbook explains FALs with the outcomes first before explaining the high level requirements and the risk process (refer to NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 7, Federation Considerations for additional federation outcomes to consider. To determine if your application requires a FAL, consider the following questions:

For _existing_ applications and defined users and transactions (Step 1):
-	Is the application integrated with any type of agency enterprise single sign-on solution? 
-	Is the application integrated with any government or commercial identity provider?
-	For organizational government users and transactions, is the application integrated with an employee’s network logon? 

For _new_ applications and defined users and transactions (Step 1):
-	Do the same users access other agency applications and could the user experience for identity and authentication be streamlined? 

If your agency and application owner answers “Yes” to any of these questions, then the application is federated, _or could be federated_ during the solution definition step (Step 3), and needs a FAL defined for each user community and transaction. 

{% include alert-info.html heading="Key Point" content="Applications that don’t implement a federated capability document the rationale in the final Digital Identity Acceptance Statement.<br><br>FAL1 and FAL2 are good for most use cases across the federal government. Agencies and application owners should consider implementations based on the community of users and transactions." %}

FALs are implemented using standard-based protocols across the federal government. These protocols are commonly used in many applications and transactions globally and are routinely supported in commercial off-the-shelf (COTS), native cloud software-as-a-service, and consumer and enterprise mobile applications. Each FAL defines minimum requirements for how the integrations are performed and the requirements if the user’s information is passed between applications. For example, for some implementations, the federation assurance levels map to commonly used federation protocols such as OpenID Connect (OIDC) and Security Assertion Markup Language (SAML). How those implementations are done maps to the increasing FAL options. 

Figure 6 explains the concept of the three Federation Assurance Levels in example terms. Refer to NIST Special Publication 800-63-3C: Digital Identity Guidelines, Federation and Assertions for the detailed requirements on Federation, Assertions, and Federation Assurance Level implementations.

[![This is a building block figure. On the left of the figure, there are a pair of hands shaking to represent an application sharing information. To the right of the shaking hands are blocks aligned under an FAL. There are increasing elements required under each successive FAL. FAL 1 includes a signed assertion. FAL 2 includes a signed and encrypted assertion. FAL 3 includes a signed and encrypted assertion with a re-verify authentication.]({{site.baseurl}}/assets/playbooks/DIRAFigure6.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure6.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 6: Federation Assurance Levels</b></p>

Figure 7 is an example of a decision tree of the risk assessment process flow that defines the Federation Assurance Levels for the communities of users and transactions in Step 1. Additional decision trees can be found in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels. The decision tree in Figure 7 is another example used by federal agencies. 

[![Figure 7 is a decision tree to select an appropriate Federation Assurance Level (FAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, are you federating? If no, a FAL assessment is not required. If yes, specify the risks (to the agency or the subject) of providing the digital service (i.e., an identity assertion is compromised) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select FAL3. If no, did you assess moderate for personal safety? If yes, select FAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select FAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select FAL2. If no, are you making personal data accessible? If yes, select FAL2. If no, are you using a front channel? If yes, select FAL2. If no, select FAL1. Reassess the FAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.]({{site.baseurl}}/assets/playbooks/DIRAFigure7.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure7.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 7: Federation Assurance Level Decision Tree</b></p>

{% include alert-info.html heading="Key Point" content="The results of a DIRA do not change established credential processes. The results impact the various credentials at a level can be used (e.g., if a DIRA arrives at IAL2, this allows the use of IAL2 but does not change the requirement of downgrading an IAL3 process to an IAL2 process)." %}

## Step 3. Determine Steps to Meet Assurance Levels

Analyze available technology and solutions at your agency, determine if they are sufficient enough to meet the application needs, and identify what you need to implement. Use data and agency enterprise defined needs when choosing solutions, including:
- Number of users by community of users;
- User experience (UX) and usability (for non-organizational users i.e., public, business, partner); and
- Direct and indirect benefits to reuse enterprise-level chosen solutions, including consolidated support desks.

Your agency may determine alternatives to the NIST-recommended guidance for the assessed assurance levels (refer to NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 5.4, Risk Acceptance and Compensating Controls) based on:  
- Your mission,
- Your risk tolerance,
- Your existing business processes,
- Special considerations for certain populations,
- The availability of data that provides similar mitigations to those described in the Digital Identity Guidelines, or
- Other capabilities unique to the agency.

Figure 8 depicts all the steps for implementing a DIRA. 

[![Figure8 is a flowchart depicting 18 steps for performing a Digital Identity Risk Assessment. Steps 1 through 3 are under the column heading Data Collection. Steps 4 and 5 are under the column heading Analysis. Steps 6 through 10 are under the column heading Review. Steps 11 through 13 are under the column heading Implementation Determination. Steps 14 and 15 are under the column heading Concurrence. Steps 16 through 18 are under the column headig Ongoing Assessment. Below the first through fifth columns there is a bar labeled Outputs. The outputs are as follows Column 1 Transaction Data, Column 2 Provisional xALs for Review, Column 3 Assessed xALs, Column 4 Implementation x ALs, Column 5 Approved Digital Identity Acceptance Statement.]({{site.baseurl}}/assets/playbooks/DIRAFigure8.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure8.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 8: Six-Step Process Displaying Requirements for Implementing a DIRA</b></p>

## Step 4. Finalize Digital Identity Acceptance Statement

Formalize the results of the assessment process with a Digital Identity Acceptance Statement (DIAS). A DIAS must include a minimum set of information about the risk assessment and the assessed and implemented assurance levels. Refer to NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 5.5, Digital Identity Acceptance Statement. 

The [Digital Identity Acceptance Statement template](../../docs/playbook-dira-dias-template.docx){:target="_blank"}{:rel="noopener noreferrer"} provides an example DIAS for agencies.  

## Step 5. Reassess

A digital identity reassessment may be time-driven or event-driven and applies to a reassessment of the DIRA.

{% include alert-info.html heading="Key Point" content="Reassess digital identity risk annually or more often for higher impact categories and transactions. A time-based assessment drives alignment with modernization initiatives, changes to technology, and changes to policies." %}

If an event triggers a security impact analysis, an agency may perform a DIRA outside the normal continuous monitoring cycle. Significant changes requiring a digital identity reassessment include changes in:
- Core mission or business functions,
- Purpose or nature of a system,
- Risk environment,
- How information, including PII, is processed, or
- How information is processed, stored, or transmitted by the system.

# Agency Process Plays

This section introduces six plays for your agency to create efficient and consistent processes for a DIRA. 

## Play 1. Streamline Risk Management and Assessment Processes

The Risk Management Framework (RMF) forms the basis of your agency application Assessment and Authorization (A&A) lifecycle. A DIRA process integrates into the routine phases of the RMF to streamline processes and enables efficient reuse of application and agency resources. Figure 9 shows an alignment of this playbook’s example DIRA process steps with the RMF. 

[![Figure 9 is a graphic representation of the DIRA process aligned with the NIST Risk Management Framework Phase. There are three concentric circles. Continuous monitoring on the outermost circle with continuous arrows representing a continuous process. The two inner circles represent the NIST RMF process aligned with DIRA. DIRA Step 1 Identify Users, Transactions, and Roles aligns with RMF Phase Categorize System. DIRA Step 2 Identify Risks and Assurance Levels aligns with RMF Phase Selecting Controls. DIRA Step 3 Determine steps to Meet Assurance Levels aligns with RMF Phase Implement Controls. DIRA Step 4 Finalize digital identity assessment statement aligns with RMF Phase Assess Controls. There is no DIRA Step that aligns with RMF Phase Authorize. DIRA Step 5 Reassess aligns with RMF Phase Monitor.etermine Assurance Levels. Step 5 is Map Transactions to Roles. Step 6 is Implement the Technology. Step 7 is Validate Requirements. Step 8 is Perform Periodic Reassessments.]({{site.baseurl}}/assets/playbooks/DIRAFigure9.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure9.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 9: Example DIRA Process Steps in Risk Management Framework Phase</b></p>

Step 1 of the example DIRA process happens in the Categorize phase. When categorizing a system (refer to Federal Information Processing Standards Publication 199 (FIPS 199):
Standards for Security Categorization of Federal Information and Information Systems, Section 3, Categorization of Information and Information Systems), application owners and security officers identify overall system data types and assign impact levels for each of the confidentiality, integrity, and availability security objectives.  

A Privacy Threshold Analysis (PTA) is typically included in this phase. The identification of the DIRA IALs, AALs, and FALs directly correlates to the collection of PII; who has access to what information; whether information is self-asserted or verified; and the risks of excessive identity proofing. 

{% include alert-info.html heading="Key Point" content="Align Step 1 in a DIRA process with the Categorize System phase of the Risk Management Framework." %}

Meanwhile, Step 4 of the example DIRA process aligns with the Assessment phase. The Digital Identity Acceptance Statement must include the IALs, AALs, and FALs where the application was assessed and the implementations made.  

Figure 10 explains the DIRA process through the Assessment phase.

[![Figure 10 is a graphic representation of the digital identity risk assessment process. Step 1 is Determine User Type. Step 2 is Define Transactions. Step 3 is Determine Impact Level for Transactions. Step 4 is Determine Assurance Levels. Step 5 is Map Transactions to Roles. Step 6 is Implement the Technology. Step 7 is Validate Requirements. Step 8 is Perform Periodic Reassessments.]({{site.baseurl}}/assets/playbooks/DIRAFigure10.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure10.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 10: DIRA Process from Data Collection to Ongoing Assessment</b></p>

Figure 11 provides additional details about the DIRA process.  

[![Figure 11 is an arrow shaped graphic that depicts the six phases of the DIRA process flow. The first phase is Data Collection. The second phase is Analysis. The third phase is Review. The fourth phase is Implementation Determination. The fifth phase is Concurrence. The sixth phase is Ongoing Assessment. There is an arrow head pointing right on the right side of the sixth phase.]({{site.baseurl}}/assets/playbooks/DIRAFigure11.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure11.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 11: Details of DIRA Process Flow from Data Collection Phase to Ongoing Assessment Phase</b></p>

## Play 2. Add Context for the Mission

Context is powerful when assessing risks, making agency risk decisions, and engaging across multi-disciplinary agency stakeholders. Standard and general government-wide policies set the foundation for many agency activities but are written for broad mission areas. Translate user types, transactions, DIRA impact levels, and risk statements into words that are applicable and useful to your agency. 

{% include alert-info.html heading="Key Point" content="Tailor context to your mission to support enterprise risk management discussions." %}

Table 4 provides examples of how agencies add agency-specific terms or context for user types, transactions, and impact levels. 

**Table 4: Example Definitions and Agency Context**

| Assessment Input | Generic Definition | Definition with Agency Context |
| ----------- | ------------ | ---------------------------------- |
| User Type | Organizational User | Employee or agency contractor with a federal agency email address (@agency.gov or @agency.mil) | 
| User Type | Non-Organizational User | Fiscal agent, grant beneficiary, veteran, healthcare worker, or public citizen | 
| Transaction | Export | Employee or agency contractors export data for use outside of the application | 
| Impact Level | Serious Injury or Death | Impact depends on whether the application provides access to law enforcement information that identifies a confidential person (i.e., improperly disclosing a confidential person’s identity puts them in physical danger) | 
| Impact Level | Harm to Agency Programs or Public Interests | Impact depends on the application’s function and its importance to agency operations | 

Table 5 provides an example of how two agencies apply context to Transactions and Impact Levels. 

**Table 5: Example Transactions and Impact Levels**

| Impact Category | Scope of Potential Risk | Agency Context: As a result of a wrong user accessing data in an application, … | User Type | Transaction Type | Agency Impact Definition |
| ----------- | ------------ | ---------------- | ----------- | ------------ | ------------------ |
| Personal Safety | Serious injury or death | Physical injury or death could occur | Organizational User | Employee or agency-contractor exports data for use outside of the system | Impact depends on whether the application provides access to law enforcement information that identifies a confidential informant (i.e., improperly disclosing a confidential criminal informant’s identity puts them in physical danger) |
| Harm to Agency Programs or Public Interests | Adverse effect on organizational operations | The agency’s mission essential functions is adversely impacted | Non-Organizational User | Individual retrieves tax information (PII) | Impact depends on the application’s function and its importance  to agency operations |

## Play 3. Use Templates 

It’s a best practice that agencies develop standardized templates to promote consistency in procedures for digital identity risk assessments. Example templates can be as simple as: 
-	Visual informational guides for what a DIRA is,
-	Informational guides on risks, 
-	Simple spreadsheets or digital surveys, and 
-	Digital Identity Acceptance Statements. 

The [Digital Identity Acceptance Statement template](../../docs/playbook-dira-dias-template.docx){:target="_blank"}{:rel="noopener noreferrer"} provides an example DIAS for agencies. 

## Play 4. Shortcut Decision Trees

All federal applications that perform digital transactions and require identity proofing or authentication require a Digital Identity Acceptance Statement, regardless of how the system is hosted. However, not all federal applications require the full example DIRA process and efforts.

Table 6 provides an example shortcut guide for determining whether to perform a full DIRA process based on application characteristics. IAL, AAL, and FAL levels in this table are examples. Applications must follow agency policies, which may be more stringent than the examples in this table.

**Table 6: DIRA Shortcut Guide**

| Application Characteristics | DIRA Required? | Minimum NIST SP 800-63 IAL, AAL, FAL Levels |
| ---------------------- | ------------ | ------------------ |
| The application has no external network connectivity, is physically isolated, and is located in a protected space. | No | N/A | 
| The application leverages the agency enterprise single sign on (SSO)/enterprise access manager for authentication of employees and contractors. | Yes | Requires proof of identity (IAL3; satisfied by the full PIV issuance processes, in accordance with government-wide policy and Office of Personnel Management (OPM) credentialing requirements for federal executive branch employees and contractors). Multi-factor authentication to agency application (AAL2) federation between agency applications (FAL2).<br><br> Additionally, requires affiliation as a federal employee or contractor. | 
| Data and other resources available are approved for public release, are intended to be freely shared, and public users aren’t required to create accounts to access this information.<br><br>Examples include:<br>• Agency primary websites (i.e., www.gsa.gov)<br>• Informational websites<br>• Open government APIs | No | Public users don’t create accounts or login. <br><br>Agency-affiliated privileged users with permissions to edit content still require higher IAL and a minimum AAL2 (two-factor). | 
| Data and other resources are intended for public release. Doesn’t include any controlled unclassified information, but allows public users to create accounts to better support the public user’s experience. | Yes | Doesn’t require proof of a real-life identity (IA 1). Single or multi-factor authentication (AAL1).| 
| Allows public users to input and access their own personally identifiable information (PII) or protected health information (PHI) for informational purposes.  The information isn’t required to be verified. The application doesn’t allow public users to access anyone else’s PII or PHI. | Yes | Doesn’t require proof of a real-life identity (IAL1). Multi-factor authentication (AAL2). | 

## Play 5. Leverage Existing Agency Tools

Leverage existing tools at your agency to automate and create repeatable and consistent DIRA processes. For example, one agency integrated the DIRA process into its Governance Risk and Compliance (GRC) tool. The agency was able to simplify integration with the Risk Management Framework (RMF) lifecycle and support the inclusion of the DIAS with other system artifacts. Agencies that use commercial GRC tools should consider integrating DIRAs into the workflows. 

## Play 6. Less Is More

A common assumption when building or buying applications for missions is that all users need accounts. Take the opportunity during the DIRA process to consider the application processes and functionality needed. Consider the mission, applications needs, and the two example questions below: 
1.	Do all users need accounts?  
2.	How many users are regularly recurring returning users? 

Reconsider the business process carefully and validate the current and future designs using data on the returning users, transaction volumes, and privacy principles. 
-	Design the business process for the user to submit information without requiring an account,
-	Limit the information required to create the account, and
-	Make most of the information requested optional.

{% include alert-info.html heading="Key Point" content="Some public, business, or partner users may only interact with the government process and application once a year or less.<br><br> Revisit your process and application, and allow users to complete the transaction once before opting in to create an account." %}

# Policy, Standards, and Guidance

This section provides links to the federal laws, policies, standards and other guidance that impact and shape DIRA implementations.  NIST also publishes useful [Frequently Asked Questions](https://pages.nist.gov/800-63-FAQ/){:target="_blank"}{:rel="noopener noreferrer"} for agencies, and an [Implementation Resource](https://www.nist.gov/system/files/documents/2020/07/02/SP-800-63-3-Implementation-Resources_07012020.pdf){:target="_blank"}{:rel="noopener noreferrer"} for solution developers. 

[Table here from DIRA PDF Appendix A]

**Table 7: DIRA Implementation Policy, Standards, and Guidance**

|    Short Name   | Full Name and Publication Date | 
| ------------------------- | ------------------------- | 
| NIST SP 800-63-3   | National Institute of Standards and Technology (NIST) Special Publication (SP) 800-63-3; [Digital Identity Guidelines](https://pages.nist.gov/800-63-3/){:target="_blank"}{:rel="noopener noreferrer"}, June 22, 2017 |
| NIST SP 800-63-3A   | National Institute of Standards and Technology (NIST) Special Publication (SP) 800-63-3; [Digital Identity Guidelines: Enrollment and Identity Proofing](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63-3.pdf){:target="_blank"}{:rel="noopener noreferrer"}, June 22, 2017 | 
| NIST SP 800-63-3B   | National Institute of Standards and Technology (NIST) Special Publication (SP) 800-63-3; [Digital Identity Guidelines: Authentication and Lifecycle](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63b.pdf){:target="_blank"}{:rel="noopener noreferrer"}, June 2017 | 
| NIST SP 800-63-3C   | National Institute of Standards and Technology (NIST) Special Publication (SP) 800-63-3; [Digital Identity Guidelines: Federation and Assertions](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-63c.pdf){:target="_blank"}{:rel="noopener noreferrer"}, June 22, 2017| 
| FISMA   | Federal Information Security Modernization Act of 2014, [44 U.S.C. § 3551 et seq., Public Law (P.L.) 113-283](https://www.congress.gov/bill/113th-congress/senate-bill/2521){:target="_blank"}{:rel="noopener noreferrer"}, December 8, 2014 | 
| HSPD-12   | Department of Homeland Security, Homeland Security Presidential Directive 12: [Policy for a Common Identification Standard for Federal Employees and Contractors](https://www.dhs.gov/homeland-security-presidential-directive-12){:target="_blank"}{:rel="noopener noreferrer"}, August 27, 2004 | 
| EO 13681   | Executive Order 13681, [Improving the Security of Consumer Financial Transactions](https://obamawhitehouse.archives.gov/the-press-office/2014/10/17/executive-order-improving-security-consumer-financial-transactions){:target="_blank"}{:rel="noopener noreferrer"}, October 2014 | 
| EO 13800   | Executive Order 13800, [Strengthening the Cybersecurity of Federal Networks and Critical Infrastructure]( https://irp.fas.org/offdocs/eo/eo-13800.pdf){:target="_blank"}{:rel="noopener noreferrer"}, May 2017 | 
| A-130   | OMB Circular A-130, [Managing Federal Information as a Strategic Resource](https://obamawhitehouse.archives.gov/sites/default/files/omb/assets/OMB/circulars/a130/a130revised.pdf){:target="_blank"}{:rel="noopener noreferrer"}, July 28, 2016 | 
| A-108   | OMB Circular A-108, [Federal Agency Responsibilities for Review, Reporting, and Publication under the Privacy Act](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/circulars/A108/omb_circular_a-108.pdf){:target="_blank"}{:rel="noopener noreferrer"}, December 2016 | 
| A-123   | OMB Circular A-123, [Management’s Responsibility for Enterprise Risk Management and Internal Control](https://www.whitehouse.gov/sites/whitehouse.gov/files/omb/memoranda/2016/m-16-17.pdf){:target="_blank"}{:rel="noopener noreferrer"}, July 15, 2016 | 
| M-19-17   | OMB M-19-17, [Enabling Mission Delivery through Improved Identity, Credential, and Access Management](https://www.whitehouse.gov/wp-content/uploads/2019/05/M-19-17.pdf){:target="_blank"}{:rel="noopener noreferrer"}, May 21, 2019 | 
| FIPS 199   | NIST FIPS Publication 199, [Standards for Security Categorization of Federal Information and Information Systems](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.199.pdf){:target="_blank"}{:rel="noopener noreferrer"}, February 2004 | 
| NIST SP 800-37   | NIST Special Publication 800-37, Revision 2, [Risk Management Framework for Information Systems and Organizations, A System Life Cycle Approach for Security and Privacy](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-37r2.pdf){:target="_blank"}{:rel="noopener noreferrer"}, December 2018 | 
| NIST SP 800-53-4   | NIST Special Publication 800-53, Revision 4, [Security and Privacy Controls for Federal Information Systems and Organizations](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r4.pdf){:target="_blank"}{:rel="noopener noreferrer"}, April 2013; Updated January 22, 2015 | 
| NIST SP 800-53A   | NIST Special Publication 800-53A, Revision 4, [Assessing Security and Privacy Controls in Federal Information Systems and Organizations: Building Effective Security Assessment Plans](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53Ar4.pdf){:target="_blank"}{:rel="noopener noreferrer"}, July 2008; Updated December 18, 2014| 
| NIST RMF Overview   | NIST [Risk Management Framework Overview](https://csrc.nist.gov/projects/risk-management/about-rmf){:target="_blank"}{:rel="noopener noreferrer"}, November 30, 2016| 

# NIST Special Publication 800-63-3 Requirements Traceability Matrix

This section includes both normative requirements and informative references from NIST SP 800-63-3: Digital Identity Guidelines. Only requirements related to the agency processes for digital identity risk assessments are included.  The Playbook Consideration column includes comments on the standards statements and alignment to this playbook’s development. 

[Table here from DIRA PDF Appendix C]

# NIST SP 800-63 Updates

In June 2017, NIST replaced Special Publication 800-63-2: Electronic Authentication Guideline with Special Publication 800-63-3: Digital Identity Guidelines. The new standard provides agencies with increased security and privacy, more flexibility to meet their mission and constituent needs, and better alignment with digital identity best practices. It outlines the digital identity risk assessment methodology that federal agencies must implement. 

NIST’s Digital Identity Guidelines identify the implementation requirements for conducting a DIRA and enable modernized risk-driven approaches for digital identities. Figure 12 depicts updated content details.

[![Figure 12 explains where the Digital Identity Guidelines information can be found.]({{site.baseurl}}/assets/playbooks/DIRAFigure12.png)]({{site.baseurl}}/assets/playbooks/DIRAFigure12.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Figure 12: Digital Identity Guideline Information Locations</b></p>

## Why Was the SP Updated?

NIST Special Publication 800-63-3 was updated to do the following: 
-	Implement Executive Order 13681: Improving the Security of Consumer Financial Transactions. 
-	Align with the current market
-	Promote innovation
-	Simplify and provide clearer guidance

## What Has Changed?

-	The DIRA process replaces the Electronic Authentication Risk Assessment process. 
-	There is a shift from levels of assurance (LOAs) to individual assurance levels (collectively known as xALs) for identity proofing, authentication, and federation.
-	The updated document introduces federation as a separate topic.

## Mix and Match Assurance Levels

The revised guidance provides individual assurance levels that can be mixed and matched, giving agencies the flexibility to deploy strong authentication without having to proof a user’s identity (i.e., if the collection of sensitive information is not required). The mix and match assurance levels allow opportunities for:
-	Greater flexibility, 
-	Greater user experience, 
-	Enhanced privacy, and 
-	Reduced risk.

