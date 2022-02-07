---
layout: page
collection: piv
title: Personal Identity Verification Interoperability for Issuers
pubdate: 2017-07
permalink: piv/piviforissuers/
sticky_sidenav: true
sidenav: piv

subnav:
    - text: Executive Summary
      href: '#executive-summary'
    - text: 1. Introduction
      href: '#1-introduction'
    - text: 2. Minimum Credential Requirements
      href: '#2-minimum-credential-requirements'
    - text: 3. Special Considerations for Federal Agencies
      href: '#3-special-considerations-for-federal-agencies
    - text: References
      href: '#appendix-a-technical-information'
---

Version 2.0.1  
July 2010

<a href="{{site.baseurl}}/assets/img/logo-gsa.png" target="_blank" rel="noopener noreferrer"><img src="{{site.baseurl}}/assets/img/logo-gsa.png" width="64" height='64' align="left" alt="U.S. General Services Administration Logo"></a>
<a href="{{site.baseurl}}/assets/img/logo-cio.png" target="_blank" rel="noopener noreferrer"><img src="{{site.baseurl}}/assets/img/logo-cio.png" width="64" height='64' align="left" alt="U.S. Federal Chief Information Officer Council Logo"></a><br><br><br>

| Version Number | Date | Change Description |
| :----------: | :-------: | -------- |
| 1.0 | 07/2010 | Initial Draft |
| 2.0 | 11/2016 | ●	Removed most duplicative references to requirements which have been stated in other government documents as authoritative<br>● Updated references to Memorandums, Standards and common terminology<br>● Added clarification for federal agencies on the boundaries of security, auditing and procurement requirements |
| 2.0.1 | 12/2016 | ● Updated Table 4 to clarify for Legislative and Judicial branches of federal government |

# Executive Summary

Federal agencies are interested in issuing and acquiring identity credentials and credential services that are not Personal Identity Verification (PIV) credentials, but are (a) technically interoperable with Federal Government PIV infrastructure, and (b) issued in a manner that allows Federal Government relying parties to trust the credentials. The PIV credential standard, Federal Information Processing Standards (FIPS) 201-2, has requirements[^1] that only federal agencies can meet to issue PIV credentials, requiring needed guidance for Issuers of PIV- Interoperable credentials. Prior guidance for the issuance of PIV-Interoperable credentials neglected to address the issuance of PIV-Interoperable credentials by federal agencies, requiring additional guidance for all issuers.

This document provides the guidance needed to assist both Federal Issuers and Non-Federal Issuers (NFI) of PIV-Interoperable (PIV-I) identity credentials in achieving credential
interoperability with the Federal Government PIV infrastructure. This document’s scope is limited to the issuance of PIV-Interoperable credentials; federal departments and agencies must continue to make their own authorization determination to allow or deny access when a PIV-Interoperable credential is used for authentication.

This document advocates a set of minimum requirements for PIV-Interoperable credentials that can be trusted by the Federal Government, and details solutions to the four barriers to interoperability that currently challenge Federal government. These four barriers are as follows:
1. **Common terminology for identity credentials and issuers** – To ensure consistency, a lexicon for differentiating a PIV credential from a credential interoperable with PIV infrastructure, and the differences between Non-Federal and Federal Issuers, has been developed.
2. **Assured identity** – The fundamental purpose of an identity credential is to establish the identity of the credential holder. Therefore, an identity credential must be issued in a federated model and consistent manner which provides the Federal Government with a requisite level of identity assurance.
3. **Technical requirements** – For identity credentials to be interoperable with the federal PIV infrastructure, basic technological requirements must be met.
4. **Security and auditing** – The boundaries for auditing and compliance requirements require clarification for federal agencies.

For additional information concerning this document, please contact icam@gsa.gov.

# 1. Introduction
## 1.1 Background

The Federal Government’s reliance (trust) on PIV credentials establishes a baseline for identity assurance, authenticator assurance, and suitability assurance. Federal agencies and issuers of identity credentials have expressed a desire to produce identity credentials that can be interoperable with Federal Government Personal Identity Verification (PIV) infrastructure and could be trusted by the Federal Government for use in authenticating to facilities, networks, and systems.

A definition for a PIV-_Interoperable_ credential for federal agencies is required to address:

*	Identity assurance requirements,<br>
*	Authenticator assurance requirements,<br>
*	Technical interoperability clarifications,<br>
*	Security and auditing clarifications, and<br>
*	Procurement clarifications.

## 1.2 Scope

This document is limited to describing identity credentials that interoperate with the Federal Government PIV infrastructure and may be accepted by the Federal Government for access to data, applications, facilities, and networks.

This document does not address the use cases for when it is appropriate or allowed for federal agencies to directly issue alternate non-PIV credentials for interoperability with PIV to employees, contractors, and affiliates.

Version 2.0 of this document has been updated to:

*	Remove many duplicative references to PIV-Interoperable requirements which have been stated in other government documents as authoritative,<br>
*	Update references and terminology, and<br>
*	Add clarification for federal departments and agencies on the scope of security, auditing, and procurement requirements.

## 1.3 Document Objectives

This document provides solutions for overcoming the barriers to federal reliance on identity credentials which are defined as interoperable with PIV. Four specific areas of concern have been identified:

1. **Common terminology for identity credentials and issuers** – To ensure consistency, a lexicon for differentiating a PIV credential from a credential interoperable with PIV infrastructure, and the differences between Non-Federal and Federal Issuers, has been developed.
2. **Assured identity** – The fundamental purpose of an identity credential is to establish the identity of the credential holder. Therefore, an identity credential must be issued in a federated model and consistent manner which provides the Federal Government with a requisite level of identity assurance.
3. **Technical requirements** – For identity credentials to be interoperable with the federal PIV infrastructure, basic technological requirements must be met.
4. **Security and auditing** – The boundaries for auditing and compliance requirements require clarification for federal agencies.

For each of these, a minimum set of requirements is described that will allow identity credentials to technically interoperate with Federal Government PIV systems and be trusted by Federal Government relying parties.

## 1.4 Assumptions

The following assumptions apply:

1. Federal departments and agencies determine the extent to which they will trust PIV- Interoperable credentials.
2. Possession of a PIV-Interoperable credential does not infer an access or authorization of any kind.
3. User privileges and entitlements (Authorization) are determined solely by the Federal Government relying party.
4. PIV-Interoperable credentials shall not be considered a substitute or alternative credential for populations otherwise subject to PIV requirements.

# 2. Minimum Credential Requirements
## 2.1 Common Terminology for Identity Credentials

To ensure consistency, a lexicon for differentiating a Federal Government PIV credential from a PIV-Interoperable credential was developed.

There is a lack of standard terminology to distinguish between characteristics of PIV credentials and PIV-Interoperable credentials in the identity credential space. This can result in confusion, uncertainty, or misunderstanding. This document resolves the terminology problem by proposing a more complete set of identity credential terms and scoping statements that unambiguously describe federal PIV credentials, federally issued PIV-Interoperable credentials, and non-Federally issued PIV-Interoperable credentials.

* **PIV credential** – An identity credential that is fully conformant with Federal Government PIV Standards including _identity assurance,_ _authenticator assurance,_ and _baseline suitability assurance._
* **PIV-Interoperable credential** – An identity credential that is conformant with the Federal Government PIV Standards for _identity assurance_ and _authenticator assurance._

Table 1 provides a summary of the identity assurance, authenticator assurance, and baseline suitability assurance requirements.

**Table 1: PIV and PIV-Interoperable Definitions**

| Assurance | Requirements Summary[^2] | PIV &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | PIV-Interoperable |
| -------------- | ------------ | ------------------| ------------------|
| **Identity Assurance:** The robustness of the identity proofing process and the binding between an authenticator and a specific individual. | 1. In-person proofing<br>2. Capture and verification of two (2) independent identity documents<br>3. Capture of biometrics | Yes | Yes |
| **Authenticator Assurance:** The robustness of the authentication process, and assurance that the user has possession of the authenticator. | 1. Public key infrastructure key pairs<br>2. Biometric<br>3. Hardware based credential | Yes | Yes |
| **Suitability Assurance:** The investigative and adjudication processes which enhance the identity assurance. Suitability is associated with a position designation and/or risk assessment for determining an individual is suitable to work for or on behalf of the Federal Government. | ● A minimum of:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;o A favorably adjudicated _National Agency Check with Inquiries_, or<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;o A favorably adjudicated Tier 1 or higher federal background investigation. | Yes | No |

All individuals issued PIV credentials are _required_ to have common, minimum suitability assurance as specified in FIPS 201-2, Section 2.1 Control Objectives. Individuals with PIV- Interoperable credentials assert no suitability assurance in a baseline, standardized manner.

Section 2.2 outlines more information for the identity assurance, authenticator assurance, and suitability assurance.

## 2.2 Trusted Identity

The fundamental purpose of an identity credential is to establish a trust foundation based on:
* the _identity assurance_ of the person, and
* the _authenticator assurance_ of the credential.

Therefore, the PIV-Interoperable credentials must be issued in a manner that provides the Federal Government with a commensurate level of trust for _identity assurance_ and _authenticator assurance._

For PIV credentials, individuals are also required to have common, minimum suitability assurance defined as:

* a baseline suitability assurance of the person to work for or on behalf of the Federal Government.

Suitability assurance may not be determined from a PIV-Interoperable credential.

### 2.2.1 PIV-Interoperable Identity Assurance

The Federal Government’s identity assurance requirements are defined in FIPS 201-2 for PIV credentials. The PIV-Interoperable credentials shall adhere to the same identity assurance requirements as PIV credentials. A summation of the identity assurance requirements is defined here for informational purposes only.

* In-person appearance and proofing
* Verification of two independent identity documents or accounts
* Capture of biometrics

The full list of requirements for identity assurance for PIV-Interoperable credentials is listed in the **X.509 Certificate Policy for the Federal Bridge Certification Authority.**

Table 2 identifies the PIV-Interoperable Level of Assurance and Identity Assurance levels as mapped to the Office of Management and Budget (OMB) Memorandums and National Institute of Standards and Technology (NIST) Special Publications.

**Table 2: Identity Assurance of PIV-Interoperable Credentials**

| Level of Assurance[^3] | Identity Assurance Level [^4] |
| -------------------- | ------------------------ | 
| Level of Assurance 4 | Identity Assurance Level 3 |

### 2.2.2 PIV-Interoperable Authenticator Assurance

The PKI certificates are where the identity assurance and authenticator assurance are asserted during use in networks, facilities, and systems. All PIV-Interoperable identity credentials must contain certificates issued from one of the Certification Authorities which operate under the Federal Public Key Infrastructure (Federal PKI) Certificate Policies.

There are two Certificate Policies which govern the Federal PKI Certification Authorities:

* Certificate Policy for the Federal Bridge Certification Authority
* Certificate Policy for the Federal PKI Common Policy Framework

There are Certification Authorities which operate and are audited for compliance to these Certificate Policies. The Certification Authorities also have Registration Authority services which may be built or operated by third-parties such as federal agencies or commercial service providers. The Registration Authority services encompass the _systems and processes_ where the initial collection of the Personally Identifiable Information (PII) is performed for the PIV or PIV- Interoperable identity assurance and lifecycle management functions.[^5] All Certification Authorities and Registration Authority components are subject to audits for compliance to management, operational, and technical controls specified in their respective Certificate Policies.[^6]

Within this boundary of more than 100 existing and audited Certification Authorities, there are options operated and available for direct use by federal departments within the Executive Branch. There are also Certification Authorities which are operated for non-federal Executive Branch entities including Legislative and Judicial Branch agencies, and State, Local, Tribal, Territorial, International, and Commercial Partners.

The Certificate Policies extension object identifier (OID) contained in the certificates asserts the identity assurance of the person presenting the credential and certificate, how the private keys are stored and managed, and how the certificate should be validated for usage.

However, the Certificate Policies extension OID for the PIV Authentication Certificates is available only to Federal Government organizations. PIV-Interoperable authentication certificates may not assert the PIV Certificate Policies OIDs used for PIV Authentication. Therefore, additional policy defines comparable Certificate Policies’ OIDs that can be trusted by the Federal Government for use in PIV-Interoperable Authentication Certificates.

The **X.509 Certificate Policy for the Federal Bridge Certification Authority** specifies the minimum requirements for the Federal Government to rely on PIV-Interoperable credentials, and includes all requirements for PIV-Interoperable credentials inclusive of:

* Certificate policy extension object identifiers,
* Clarification on identifier namespaces to be used, and
* Credential requirements for security and auditing.

All issuers of PIV-Interoperable credentials shall adhere to the requirements for PIV- Interoperable credentials outlined in the **X.509 Certificate Policy for the Federal Bridge Certification Authority.**

Operationally, the Certification Authorities and Registration Authorities that may be subordinate to the **Certificate Policy for the Federal PKI Common Policy Framework** must map their management, security, and operational controls for PIV-Interoperable credentials without needing a _cross-certificate_ directly from the Federal Bridge Certification Authority. Policy mapping may be used; the Certification Authority must receive a certificate from Common Policy Framework which maps the Federal Bridge Certification Authority policy OIDs to the issuing Certification Authority’s OIDs for PIV-Interoperable.

Table 3 identifies the PIV-Interoperable Authenticator Assurance levels as mapped to the Office of Management and Budget (OMB) Memorandums and NIST Special Publications.

**Table 3: Authenticator Assurance of PIV-Interoperable Credentials**

| Level of Assurance[^7] | Authenticator Assurance Level [^8] |
| -------------------- | ------------------------ | 
| Level of Assurance 4 | Authenticator Assurance Level 3 | 

### 2.2.3 PIV-Interoperable Suitability Assurance

Suitability assurance is defined as the investigative and adjudication processes which _enhance_ the identity assurance. These processes are used to determine suitability for granting access to federal data, applications, facilities, and networks. Only the Federal Government may determine the fitness or suitability of an individual for access to Federal Government assets.

PIV-Interoperable processes are unable to mirror the suitability assurance processes employed for the PIV credential. PIV-Interoperable credentials assert no suitability assurance in a _baseline, standardized manner._

A Federal Government relying party may associate the PIV-Interoperable credential with additional off-credential information to determine the fitness or suitability of the requested access. Examples of off-credential information could be a record check against investigation databases, an entitlements attribute, or other manual or automated processes.

PIV-Interoperable credentials may be appropriate for situations where an agency has determined that a PIV credential is not warranted, but the individual requires access. Such situations may include, but are not limited to:

* Temporary/seasonal employees, visiting scientists and guest researchers, or contractor personnel requiring access for less than six (6) months;
* Non-U.S. nationals with insufficient residency in the U.S. to satisfactorily conduct the background investigation; and
* Personnel operating outside the contiguous U.S. under special risk security considerations, as outlined in FIPS 201-2.

A standardized set of procedures and processes for suitability assurance covering any or all of these possible use cases is outside the scope of this document.

Where suitability is a concern for a federal agency, the agency may require further suitability checks prior to granting any access. This document does not prohibit a suitability and fitness determination from being required by federal departments and agencies prior to issuing a federal PIV-Interoperable credential _or_ granting any access to an individual with a PIV-Interoperable credential.

## 2.3 Federal Issuers and Non-Federal Issuers for PIV-Interoperable Credentials

For PIV-Interoperable credentials, there may be Federal Issuers and Non-Federal Issuers who participate. Many documents have asserted the term “Non-Federal Issuer” or NFI as synonymous with a PIV-Interoperable credential; the two terms are different and there is a need to clarify the terminology.

Two (2) sample scenarios are outlined in Table 4 to clarify the difference between a NFI and a Federal Issuer of PIV-Interoperable credentials.

**Table 4: Scenarios of a Non-Federal and Federal Issuer of PIV-Interoperable Credentials**

|                  | Scenario A: Non-Federal Issuer | Scenario B: Federal Issuer |
|------------------|--------------------------------------|--------------------------------------|
| **Description**      | Federal Agency **A** has affiliates or service providers who have persons who manage data systems, or need access to the federal networks or facilities | Federal Agency **B** has affiliates or persons who manage data systems, or need access to the federal networks or facilities |
| **Scenario Outline** | Federal Agency A:<br><br>1. Requests partners, affiliates, or service providers to have their contracted or employee personnel obtain PIV-I credentials<br><br>2. Provides the request through a Department or Agency-level Policy, Memorandum, or contract action with the affiliate or service provider<br><br>3. The partner, affiliates, or service provider chooses the PIV-I service or builds their own, and makes any contractual or other arrangements with the PIV-I service | Federal Agency B: <br><br>1. Selects a PIV-I credentialing service to use<br><br>2. Pays for or builds the PIV-I service<br><br>3. Authorizes and directs persons to use a designated PIV-I service and receive PIV-I credentials<br><br>4. Has responsibility for the sponsoring of persons, lifecycle management, and other activities including revoking the credentials after the person terminates any service |
| **Type**             | _Non-Federal Issuer of PIV-Interoperable Credentials_ | _Federal Issuer of PIV-Interoperable Credentials_ |
| **Examples**         | ● State, Local, Tribal, and Territorial partners<br>● Aerospace and Defense partners<br>● Financial Services partners | ● Federal Agency B has determined that persons under their authority require PIV- Interoperable credentials to meet a use case where PIV credentials do not apply |


## 2.4 Technical Requirements

(text here)

### 2.4.1 Visual Distinction

(text here)

### 2.4.2 Identifier Namespace

(text here)

# 3. Special Considerations for Federal Agencies

(text here)

## 3.1	Auditing Requirements

(text here)

## 3.2 Acquiring PIV-Interoperable Services

(text here)

# Appendix A: Technical Information

(text here)

# Appendix B: Glossary

(possibly do glossary like PACS glossary; not in a table)

# Appendix C: Acronyms

(table here)

# Appendix D: Document References

(text here)

# Footnotes

(text here)
