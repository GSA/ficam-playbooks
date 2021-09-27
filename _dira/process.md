---

layout: page
navtitle: Digital Identity Risk Assessment
title: DIRA Process
collection: playbooks
permalink: DIRA/process/
sticky_sidenav: true
sidenav: DIRA

subnav:
  - text: Step 1
    href: #step-1
  - text: Step 2
    href: #step-2
  - text: Step 3
    href: #step-3
  - text: Step 4
    href: #step-4
  - text: Step 5
    href: #step-5

---

The DIRA process begins when a new application or system is identified or a time-driven or event-driven reassessment is triggered. Once it is determined that a DIRA is needed, application data is identified, collected, and analyzed to determine the assurance levels, and produce a Digital Identity Assessment Statement (DIAS), as shown in Figure 1.

[![This is a circle figure with five steps. The DIRA process starts at the top of the circle when a new application or system is identified or when a time or event-based reassessment is triggered. Step 1 is Identify User, Transactions, and Roles. Step 2 is Identify Risks and Assurance Levels. Step 3 is Determine Steps to Meet Assurance Levels. Step 4 is Finalize Digital Identify  Assessment Statement. Step 5 is Reassess. Return back to Step 1 based on new application or event trigger.](../../assets/dira/process_DIRAFigure1.png)](../../assets/DIRA/process_DIRAFigure1.png){:target="_blank"}{:rel="noopener noreferrer"}

A high-level DIRA process includes five steps:
1)	Identify Users, Transactions, and Roles
2)	Identify Risks and Assurance Levels
3)	Determine Steps to Meet Assurance Levels
4)	Finalize Digital Identity Assessment Statement
5)	Reassess

## Step 1: Identify Users, Transactions, and Roles 

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

## Step 2: Identify Risks and Assurance Levels 

Determine the digital identity risk for each assurance category by assessing the impacts for each community of user, user type, common role, and transactions identified in Step 1.  

-	**Identity Assurance Levels (IALs)** indicate the level of confidence in a claimed identity. 
-	**Authenticator Assurance Levels (AALs)** indicate authentication requirements.
-	**Federation Assurance Levels (FALs)** indicate the level of confidence in an assertion used to communicate identity or authentication information across applications or across agencies. 

The risks and impact assessment considers the risks to both the agency and the user for the transactions. The risk to one can be significant while not negatively impacting the other at all. It’s common for government applications to have different assurance levels based on differing impacts and risks for each community of users and transactions.

{% include alert-info.html heading="Key Point" content="The impact categories and definitions used in the DIRA process are the same used to determine the _overall_ application system categorization for impacts to confidentiality, integrity, and availability (a FIPS 199 assessment).<br><br>However, your overall application system categorization (FIPS 199) is often _different_ than the risks and impacts for the identity and authenticator assurance levels for communities of users and transactions for the DIRA." %}

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

[![Figure 2 is a building block figure. A user is on the right of the figure and to the left of the user are different data elements provided by a user. Each IAL includes addition data to increase the assurance. IAL 1 data includes Display Name & Email Address. IAL 2 data includes confirmed through record checks through virtual or in-person, address of record, and real name & email address. IAL 3 data includes confirmed through record checks and in-person, biometric, address of record, and real name & email address.](../../assets/dira/process_DIRAFigure2.png)](../../assets/DIRA/process_DIRAFigure2.png){:target="_blank"}{:rel="noopener noreferrer"}

Figure 3 is an example of a decision tree of the risk assessment process flow that defines the Identity Assurance Levels for the communities of users and transactions in Step 1. Additional decision trees are in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels.

[![Figure 3 is a decision tree to select an appropriate Identity Assurance Level (IAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, do you need any Personally Identifiable Information (PII) or Protected health information (PHI)? If no, select IAL1. If yes, do you need the PII/PHI to be validated? If no, select IAL1. If yes or if you don’t know, specify the risks (to the agency or the subject) of providing the digital service (i.e., a person falsely claiming an identity) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select IAL3. If no, did you assess moderate for personal safety? If yes, select IAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select IAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select IAL2. If no, are you making personal data accessible? If yes, select IAL2. If no, select IAL1. Reassess the IAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.](../../assets/dira/process_DIRAFigure3.png)](../../assets/DIRA/process_DIRA Figure3.png){:target="_blank"}{:rel="noopener noreferrer"}

### Authenticator Assurance

Authenticator Assurance Levels define the strength of the authentication process. AALs mitigate potential authentication errors (i.e., an attacker accessing a user’s account).
-	Authenticator Assurance is: “Is this the same user as before?”
-	Impacts are: “What are the risks to the government or to you if you are not the same user as before?”

At Authenticator Assurance Level 1 (AAL1), a user might only use a username and password. At Authenticator Assurance Level 2 (AAL2), a user has two factors, including a factor such as a one-time password (OTP) managed by a mobile application on a personal or government mobile phone (refer to NIST Special Publication 800-63-3B: Digital Identity Guidelines, Authentication and Lifecycle Management, Section 4, Authenticator Assurance Level requirements). 

{% include alert-info.html heading="Key Point" content="Two-factor authentication is rapidly becoming the expected default for applications.<br><br>Recurring public and other non-organizational users may want to create an account. Agencies and application owners should strongly consider always allowing and providing two-factor options.<br><br>For employees and other organizational government users, two-factor authentication is a government-wide policy requirement." %}

Figure 4 explains the concept of the three Authenticator Assurance Levels in example terms of the authentication (refer to NIST Special Publication 800-63-3B: Digital Identity Guidelines, Authentication and Lifecycle Management, Section 4, Authenticator Assurance Level requirements).

[![This figure is a building block figure. A user is on the right of the figure and to the left of the user are different authenticator elements used to log in. Each AAL includes an authentication factor to increase the assurance. AAL 1 includes a single factor. AAL 2 includes two factors. AAL 3 includes two factor with cryptographic hardware.](../../assets/dira/process_DIRAFigure4.png)](../../assets/DIRA/process_DIRA Figure4.png){:target="_blank"}{:rel="noopener noreferrer"}

Figure 5 is an example of the risk assessment process flow that defines the Authenticator Assurance Levels for the community of users and transactions in Step 1. Additional decision trees can be found in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels. The decision tree in Figure 5 is another example used by federal agencies.

[![Figure 5 is a decision tree to select an appropriate Authenticator Assurance Level (AAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, specify the risks (to the agency or the subject) of providing the digital service (i.e., a false claimant using an identity that is not theirs) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select AAL3. If no, did you assess moderate for personal safety? If yes, select AAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select AAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select AAL2. If no, are you making personal data accessible? If yes, select AAL2. If no, select AAL1. Reassess the AAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.](../../assets/dira/process_DIRAFigure5.png)](../../assets/DIRA/process_DIRA Figure5.png){:target="_blank"}{:rel="noopener noreferrer"}

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

[![This is a building block figure. On the left of the figure, there are a pair of hands shaking to represent an application sharing information. To the right of the shaking hands are blocks aligned under an FAL. There are increasing elements required under each successive FAL. FAL 1 includes a signed assertion. FAL 2 includes a signed and encrypted assertion. FAL 3 includes a signed and encrypted assertion with a re-verify authentication.](../../assets/dira/process_DIRAFigure6.png)](../../assets/DIRA/process_DIRA Figure6.png){:target="_blank"}{:rel="noopener noreferrer"}

Figure 7 is an example of a decision tree of the risk assessment process flow that defines the Federation Assurance Levels for the communities of users and transactions in Step 1. Additional decision trees can be found in NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 6, Selecting Assurance Levels. The decision tree in Figure 7 is another example used by federal agencies. 

[![Figure 7 is a decision tree to select an appropriate Federation Assurance Level (FAL) for each user community and transactions. Starting from the top of the decision tree, for each user community and transactions, are you federating? If no, a FAL assessment is not required. If yes, specify the risks (to the agency or the subject) of providing the digital service (i.e., an identity assertion is compromised) by determining the risk impact value for each of the impact categories in Table 3: Impact Definitions. Did you assess at high for any of the impact categories? If yes, select FAL3. If no, did you assess moderate for personal safety? If yes, select FAL3. If no, did you assess moderate for any of the remaining impact categories? If yes, select FAL2. If no, did you assess low for harm to agency programs or public interests, unauthorized release of sensitive information, personal safety, or civil or criminal violations? If yes, select FAL2. If no, are you making personal data accessible? If yes, select FAL2. If no, are you using a front channel? If yes, select FAL2. If no, select FAL1. Reassess the FAL level for each user community and transactions based on agency policies or when a significant change to the transaction occurs, whichever comes first.](../../assets/dira/process_DIRAFigure7.png)](../../assets/DIRA/process_DIRA Figure7.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 3: Determine Steps to Meet Assurance Levels

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

[![Figure 8 is a flowchart depicting 18 steps for performing a Digital Identity Risk Assessment. Steps 1 through 3 are under the column heading Data Collection. Steps 4 and 5 are under the column heading Analysis. Steps 6 through 10 are under the column heading Review. Steps 11 through 13 are under the column heading Implementation Determination. Steps 14 and 15 are under the column heading Concurrence. Steps 16 through 18 are under the column headig Ongoing Assessment. Below the first through fifth columns there is a bar labeled Outputs. The outputs are as follows Column 1 Transaction Data, Column 2 Provisional xALs for Review, Column 3 Assessed xALs, Column 4 Implementation x ALs, Column 5 Approved Digital Identity Acceptance Statement.](../../assets/dira/process_DIRAFigure8.png)](../../assets/DIRA/process_DIRA Figure8.png){:target="_blank"}{:rel="noopener noreferrer"}

## Step 4: Finalize Digital Identity Acceptance Statement

Formalize the results of the assessment process with a Digital Identity Acceptance Statement (DIAS). A DIAS must include a minimum set of information about the risk assessment and the assessed and implemented assurance levels. Refer to NIST Special Publication 800-63-3: Digital Identity Guidelines, Section 5.5, Digital Identity Acceptance Statement. 

The [Digital Identity Acceptance Statement template](../../docs/dira-dias-template.docx){:target="_blank"} provides an example DIAS for agencies.   

## Step 5
