---
layout: page
title: Services Framework
collection: arch
permalink: /arch/services/
sticky_sidenav: true
sidenav: arch
pdf: "docs/ficam-arch.pdf"

subnav:
  - text: Identity Management
    href: '#identity-management'
  - text: Credential Management
    href: '#credential-management'
  - text: Access Management
    href: '#access-management'
  - text: Federation
    href: '#federation'
  - text: Governance
    href: '#governance'
---

The Services Framework identifies the services that provide functionality within the scope of ICAM. The Services Framework is a tool for you to help translate between business requirements and technical solutions.

The Services Framework is designed for ICAM program managers and information technology enterprise architects.

## FICAM Practice Areas

<img src="{{site.baseurl}}/assets/arch/services/ServicesOverview.png" alt="Five boxes that each correspond to a FICAM practice area or supporting element. Each box lists the agency services that correspond to that area. You can find the services and definitions in the following pages." width="560" height="466">

## FICAM Services

<img src="{{site.baseurl}}/assets/arch/services/ServicesDefinitions.png" alt="Five boxes that each correspond to a FICAM practice area or supporting element. Each box includes the definitions for the agency services that correspond to that area. You can find the services and definitions in the following pages." width="560" height="314">

## Identity Management

<img src="{{site.baseurl}}/assets/arch/services/IdentityManagementServices.png" alt="An orange box with the list of Identity Management services defined later in the body text of this page." width="260" height="333" align="right" style="padding-left:30px">

Identity Management is how an agency collects, verifies, and manages attributes and entitlements to establish and maintain enterprise identities for federal government employees, contractors, and authorized mission partners. This service does not apply to public or consumer identity management.

An enterprise identity record is the set of attributes, or characteristics, that describe a person within a given context:

- Your identity within your agency’s Human Resources (HR) system is different from your personal identity at your bank.
- A person’s identity as a government contractor is different from their identity as an Army Reservist.

Although your identity remains the same over time, it evolves as your attributes change, such as when you get a promotion, change your name, receive additional training, or retire.

Agencies should manage identity attributes as centrally as possible and distribute them as needed. The following are some examples of identity attributes:

- *Core identity attributes* - First name, last name, and address of record.
- *Contact attributes* - Physical location, government phone number, and government email address.
- *Authorization attributes* - Clearance, training, and job codes.

Entitlements are a specific type of authorization attributes that represent an application permission. Entitlements management is the act of managing those permissions. An agency may group multiple entitlements into a specific role or group to streamline provision and deprovision activities as well as for auditing and reporting. For example, a new employee may require access to ten core enterprise applications on the first day of work. An agency can create a new employee group with new employee entitlements and automate provisioning to the ten core applications rather than treat them as individual access requests.

Attributes and entitlements are created or aggregated through a number of manual and automated mechanisms. Mechanisms may include: 
- Use a Single Sign-On tool to aggregate application access entitlements.
- Allow employees to update contact attributes in a employee record.
- Automated integration between a training system and a identity governance and administration tool to create and update annual security training.

Identity proofing is how an agency verifies an enterprise identity. The complexity of this process depends on the Identity Assurance Level (IAL) you require for an identity. Federal agencies require a minimum IAL3 for employees and contractors. For example, a federal employee or contractor presents identity attributes via a driver's license or utility bill. The agency verifies the identity documents and the individual's photo (biometric).

An identifier is a unique attribute used to locate an identity in a system:

- While your agency may issue Personal Identification Verification (PIV) cards to multiple people named John Smith, each has a different PIV card number.
- While your agency may have more than one employee named Jane Smith, each employee has a unique email address tied only to their identity.

### Identity Management Services

The Identity Management services in the Federal ICAM architecture include Creation, Identity Proofing, Provisioning, Maintenance, Identity Aggregation, and Deactivation. These services are sometimes collectively known as **Identity Lifecycle Management**.

<img src="{{site.baseurl}}/assets/arch/services/IdentityManagementServiceDefinitions.png" alt="An orange box with the Identity Management service definitions, which are listed in the following body text." width="560" height="61">

| Service | Description | Keywords |
| --- | ------ | -----|
| Creation | Establish an identity made of attributes that define a person or entity. | Identity Record, Authoritative Source |
| Identity Proofing | Use identity attributes to connect a digital identity to a real-world entity. | Source Document Validation, Remote Proofing, In-Person Proofing|
| Provisioning | Create, manage, and delete accounts and entitlements. | Identity Lifecycle Management, Workflow, Deprovisioning, Account Management, Account Creation, Entitlements Management |
| Maintenance | Maintain accurate and current attributes in an identity record over its lifecycle. | Identity Lifecycle Management, Updating, Attribute Management |
| Identity Aggregation | Find and connect disparate identity records for the same person or entity. | Identity Reconciliation, Identity Resolution, Account Linking|
| Deactivation | Deactivate or remove enterprise identity records. | Identity Lifecycle Management, Suspension, Archiving, Deletion |

## Credential Management

<img src="{{site.baseurl}}/assets/arch/services/CredentialManagementServices.png" alt="A green box with the list of Credential Management services defined later in the body text of this page." width="260" height="333" align="right" style="padding-left:30px">

Credential Management is how an agency issues, manages, and revokes credentials bound to enterprise identities.

A credential is a data structure that authoritatively binds an authenticator to an existing identity using one or more identifiers. 

The following are types of authenticators:

- Something you know, like a password or PIN.
- Something you have, like a private key or One-Time Password (OTP) generator.
- Something you are, like a fingerprint or iris. 

The Authenticator Assurance Level (AAL) determines the authenticators associated with a credential. Federal government-wide policy requires a minimum Authenticator Assurance 
Level 2 for employees and contractors.

The following are some examples of credentials:

- You might use an agency-issued smart card, such as a PIV or CAC, that includes a picture and cryptographic key pairs to assert your identity at a federal facility.
- You might use a combination of credentials, like a username/password with an OTP generated by a mobile application, to assert your identity to a federal web 
application.

Unlike identities, credentials can expire. If an enterprise identity continues past a credential’s expiration date, the issuing agency can issue a new credential.

### Credential Management Services

The Credential Management services in the FICAM architecture include Sponsorship, Registration, Generation & Issuance, Maintenance, and Revocation.

<img src="{{site.baseurl}}/assets/arch/services/CredentialManagementServiceDefinitions.png" alt="A green box with the Credential Management service definitions, which are listed in the following body text." width="560" height="61">

| Service | Description | Keywords |
| --- | ------ | -----|
| Sponsorship | Formally establish that a person or entity requires a credential. | Sponsor, Authorizing Official, Affiliation, Request |
| Registration | Collect the information needed from a person or entity to issue them a credential. | Enrollment |
| Generation & Issuance | Assign a credential to a person or entity. | Activation, Token, Authenticator |
| Maintenance | Maintain a credential throughout its lifecycle. | Renewal, Reset, Suspension, Reissuance |
| Revocation | Revoke a credential from a person or entity, or deactivate an authenticator. | Termination |

## Access Management

<img src="{{site.baseurl}}/assets/arch/services/AccessManagementServices.png" alt="A blue box with the list of Access Management services defined later in the body text of this page." width="260" height="333" align="right" style="padding-left:30px">

Access Management is how an agency authenticates enterprise identities and authorizes appropriate access to protected services.

Policy administration is a combination of laws, regulations, rules, and agency policies that secure access to agency services. Your agency determines the requirements for an individual to access each resource category, and they can be as simple or as complex as you need. The following are some examples of access requirements:

- “Grant access to anyone on this list of people.”
- “Grant access to any agency employee or contractor with an authenticated PIV card.”
- “Grant access to anyone who is a federal employee, GS-12 or higher, cleared Top Secret, trained in first aid, and certified as a project manager.”

One challenge to overcome in providing access services is conducting an application discovery and inventory for both physical and logical access. For logical access, see the [Application Inventory and Identity Risk Analysis section of the Enterprise Single Sign-On Playbook.]({{site.baseurl}}/playbooks/sso/#step-2-plan-application-integration){:target="_blank"}{:rel="noopener noreferrer"}

### Authentication
 
Authentication is how you verify the claimed identity of someone trying to access an agency resource. Typically, you’ll verify an identity using an authenticator associated with a credential. To determine the appropriate authenticator level, use the [Digital Identity Risk Assessment Playbook]({{site.baseurl}}/playbooks/dira/){:target="_blank"}{:rel="noopener noreferrer"}

Authentication is generally a two-step process:

> *Step 1.* Authenticate the credential itself:
- Did a trusted organization issue the credential?
- Has the credential expired?
- Has the credential been revoked, voided, or tampered?

> *Step 2.* Ensure the individual that the credential was issued to is the same individual that is presenting it:
- Do the photo and attributes on the credential match the person who presented it?
- Does the person know the PIN for the credential?
- Does the person have the private key on the smart card for the certificate presented to a website?

### Authorization

Authorization is how you decide whether you should allow someone to access an agency resource. Access requirements usually dictate whether you’ll allow someone to:

- Read or modify a certain document.
- Access an agency website.
- Enter an agency facility or location.

Usually, authorization occurs immediately after authentication. When you log in to a service, you present your credentials and the service confirms your credentials are valid (authentication) and grants or denies you access based on your assigned permissions (authorization).

Authorizations are based on progressive fine-grained access models. The majority of agencies implement role-based access and are moving towards more fine-grained access such as attribute-based or risk adaptive as outlined in the [Federal Zero Trust Strategy](https://zerotrust.cyber.gov/federal-zero-trust-strategy/){:target="_blank"}{:rel="noopener noreferrer"}. While there are defined access models, vendors may implement them in different or overlapping ways. Ensure your agency develops use cases and understands how a vendor meets the use case.

| | Less Fine-Grained | --> | --> | More Fine-Grained |
| |:----:|:----:|:----:|:----:|
| Access Model | Access Control Lists (ACLs) | Role-Based Access Control (RBAC) | Attribute-Based Access Control (ABAC)| Risk Adaptive Access Control (RAAC) |
| Description | A static list of entities with their access rights. | Access based on a user's static pre-defined role. | Access based on a user's assigned attributes which may be static or dynamic. | Access based on dynamic risk factors. |
| Example | Allow Jane Doe access to email application | Jane Doe is assigned the user role "New Employee" which grants access to email and sharepoint. | Allow Jane Doe to access email if on a government device (device attribute) and in the United States (location attribute). | If Jane Doe is in assigned work location, allow email access from any managed device. If Jane Doe is not in assigned work location, only allow email access from a government device. |

Each of these authorization models has benefits and limitations. The policies and access requirements defined by agency business owners help inform the model used to best suit their needs. More robust access control models, such as ABAC, can help agencies with improved automation and are increasingly adopted by cloud-native and cloud-friendly services.

### Access Management Services

The Access Management services in the federal ICAM architecture include Policy Administration, Authentication, Authorization, and Privileged Access Management.

<img src="{{site.baseurl}}/assets/arch/services/AccessManagementServiceDefinitions.png" alt="A blue box with the Access Management service definitions, which are listed in the following body text." width="560" height="61">

| Service | Description | Keywords |
| --- | ------ | -----|
| Digital Policy Administration | Create and maintain the technical access requirements that govern access to protected agency services. | Policy Decision, Policy Enforcement | 
| Authentication | Verify that a claimed identity is genuine based on valid credentials. | Validation, Two-Factor, Multi-Factor |
| Authorization | Grant or deny access requests to protected agency services based on access requirements, identity attributes, and entitlements. | Policy Decision, Policy Enforcement | 
| Privileged Access Management | Protect access to accounts that have access permissions that can affect IT system configurations and data security (e.g., superusers, domain administrators, or global administrators). | Privileged Identity Management, Privileged Account Management, Administration, Superuser |

## Federation

<img src="{{site.baseurl}}/assets/arch/services/FederationServices.png" alt="A gray box with the list of Federation services defined later in the body text of this page." width="260" height="333" align="right" style="padding-left:30px">

Federation is the technology, policies, standards, and processes that allow an agency to accept digital identities, attributes, and credentials managed by other agencies.

Federation has many different applications, including:

- *Accepting an authentication transaction from another organization:*

> Agency A authenticates one of its users and passes identity attributes and transaction details to Agency B. Agency B grants access to an application        for that identity.

- *Accepting specific characteristics (i.e., attributes such as identifiers) describing an individual from another organization:*

> An individual can use their agency-issued credential containing an internal identifier(s) to directly log in to a different agency’s online service. The    online service registers the identifier(s) in their system for future use.

### Federation Services
The Federation services in the FICAM architecture include Policy Alignment, Authentication Broker, and Attribute Exchange.

<img src="{{site.baseurl}}/assets/arch/services/FederationServiceDefinitions.png" alt="A gray box with the Federation service definitions, which are listed in the following body text." width="560" height="61">

| Service | Description | Keywords |
| --- | ------ | -----|
| Policy Alignment | Develop relationships and a common understanding between parties by establishing authorities, policies, standards, and principles. | Trust Relationship | 
| Authentication Broker | Transform an authentication event into an alternative format, such as an assertion, containing claims about the entity and the authentication transaction, to grant access to a resource. | Assertion Service, Federation Assertion, Security Token Service |
| Attribute Exchange | Discover and acquire identity or other attributes between different systems to promote access decisions and interoperability. | Attribute Definition | 

## Governance

<img src="{{site.baseurl}}/assets/arch/services/GovernanceServices.png" alt="A navy box with the list of Governance services defined later in the body text of this page." width="260" height="333" align="right" style="padding-left:30px">

Governance is the set of practices and systems that guides ICAM functions, activities, and outcomes.

To perform effective governance, agencies must collect data about ICAM functions from many sources, such as policies and entitlements stores, and analyze this data. Proper data analytics help agencies monitor compliance with established information security policies. 

If your agency identifies problems during data collection and analysis, you should remediate these issues as quickly as possible. Real-time monitoring and risk mitigation is crucial to ensure employees and contractors have only the appropriate access, following the principle of least privilege.

### Governance Services

The Governance services in the FICAM architecture include Identity Governance, Analytics, and Mitigation.

<img src="{{site.baseurl}}/assets/arch/services/GovernanceServiceDefinitions.png" alt="A navy box with the Governance service definitions, which are listed in the following body text." width="560" height="61">

| Service | Description | Keywords |
| --- | ------ | -----|
| Identity Governance | The systems, solutions, and rules that link enterprise personnel, applications, and data to help agencies manage access and risk. | Management Framework, Rules and Procedures, Access Reviews and Recertifications | 
| Analytics | Leverage continuous analytics data to identify if someone has entitlements that conflict with access requirements. | Data collection, Monitoring, Review, Data Certification, Auditing and Reporting | 
| Mitigation | Correct the problems and address risks, discovered by analysis, that may occur during standard operations. | Redress, Remediation |
