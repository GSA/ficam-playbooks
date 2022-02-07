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

(text here)

### 2.2.2 PIV-Interoperable Authenticator Assurance

(text here)

### 2.2.3 PIV-Interoperable Suitability Assurance

(text here)

## 2.3 Federal Issuers and Non-Federal Issuers for PIV-Interoperable Credentials

(text here)

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
