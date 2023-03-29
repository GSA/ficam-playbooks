---
layout: page
collection: playbooks
title: Digital Autopen Playbook
pubdate: 2023-03
type: Markdown
permalink: /playbooks/autopen/
description: This playbook outlines the process for an agency to implement a Digital Autopen for Federal Register documents.
sticky_sidenav: true
sidenav: ilm

subnav:
  - text: Executive Summary
    href: '#executive-summary'
  - text: The Digital Autopen
    href: '#the-digital-autopen'
  - text: Step 1. Define the Agency Process
    href: '#step-1-define-the-agency-process'
  - text: Step 2. Define Controls
    href: '#step-2-define-controls'
  - text: Step 3. Obtain a Digital Autopen Certificate
    href: '#step-3-obtain-a-digital-autopen-certificate'
  - text: Summary
    href: '#summary'
  - text: Appendix A. References
    href: '#appendix-a-references'
  - text: Appendix B. Policy Recommendations
    href: '#appendix-b-policy-recommendations'
  - text: Appendix C. Templates
    href: '#appendix-c-templates'
---

Version 1.0  
March 29, 2023

The Delegated Digital Signature Working Group of the Federal Chief Information Security Officer Council Identity, Credential, and Access Management Subcommittee developed this playbook to outline the process for a federal agency to implement a digital autopen for *Federal Register* documents.

<img src="{{site.baseurl}}/assets/img/logo-gsa.png" width="64" height='64' align="left" alt="U.S. General Services Administration Logo">
<img src="{{site.baseurl}}/assets/img/logo-cio.png" width="64" height='64' align="left" alt="U.S. Federal Chief Information Officer Council Logo">
<br><br><br>

| Version Number | Date | Change Description |
| :----------: | :-------: | -------- |
| 1.0 | 06/30/2022 | Initial Draft. |

## Executive Summary

This playbook outlines the process for an agency to implement a Digital Autopen for *Federal Register* documents. Federal regulatory agencies issue regulations based on laws enacted by Congress or an executive power. Those regulations may be digitally signed and submitted electronically to the Office of the Federal Register (OFR) for publication.  OFR requires all documents submitted for publication to be signed by an official authorized to act for the agency. When an official is unavailable or unable to sign a document, they may authorize another agency employee to use a digital autopen to affix the official’s digital signature to the document. This playbook assumes that the agency has existing rules governing the delegation of authority and builds upon such rules to outline a three-step process to create a digital autopen to sign a Federal Register document. 

1. [Define the agency process](#step-1-define-the-agency-process) to delegate signing Federal Register documents. 
2. [Define controls](#step-2-define-controls) to ensure the certificate and associated key are used only for the intended purpose. 
3. [Obtain a role-based digital signature certificate](#step-3-obtain-a-digital-autopen-certificate) from a Federal Public Key Infrastructure (PKI) Shared Service Provider. 

This playbook recommends using a role-based signature certificate issued to a hardware device (e.g., smart card, USB hardware device, or other FIPS–140 Level 2  certified hardware) from a [Federal PKI Certification Authority](https://www.idmanagement.gov/buy/trust-services/#government-identity-services){:target="_blank"}{:rel="noopener noreferrer"}. [Federal Agency Certification Authorities](https://playbooks.idmanagement.gov/fpki/ca/#all-federal-pki-certification-authorities){:target="_blank"}{:rel="noopener noreferrer"} may also issue this certificate on their own. The digital autopen certificate can only digitally sign documents. An agency should consider additional controls to limit its use only to sign *Federal Register* documents. This playbook supports [OMB Circular A-130 goals](https://obamawhitehouse.archives.gov/sites/default/files/omb/assets/OMB/circulars/a130/a130revised.pdf){:target="_blank"}{:rel="noopener noreferrer"}, including developing and implementing processes to support employee digital signatures.

Send any questions on the process to ICAM at gsa.gov. 

### Key Terms

- Authorizing sponsor – The federal official authorized to sign Federal Register documents.
- Digital autopen - The digital equivalent of a physical autopen solution.
- Digital autopen certificate - A Federal PKI role-based digital signature certificate used to sign Federal Register documents when approved by the authorizing sponsor.
- Digital autopen recipient - The person identified by the authorizing sponsor to use the digital autopen to affix the authorizing sponsor's signature to a Federal Register document.
- Federal PKI - The Federal PKI is a network of certification authorities (CAs) that issue, PIV credentials and person identity certificates, PIV-Interoperable credentials and person identity certificates, and other person identity certificates. For more information n the Federal PKI contact FPKI at gsa.gov.
- *Federal Register* document - A document drafted for the express purpose of publication in the Federal Register. 
- Office of the Federal Register (OFR) - The agency responsible for publishing the Federal Register.

### Disclaimer

The Delegated Digital Signature Working Group of the Federal Chief Information Security Officer Council ICAM Subcommittee developed this Playbook. U.S. Federal Executive Branch agencies can use this Playbook to supplement existing electronic signature policy and implement specific procedures to create a digital autopen to sign Federal Register documents. This Playbook is not official policy, mandated action, or provides authoritative information technology terms. It includes best practices to supplement existing federal policies and builds upon Office of Management and Budget Memorandum 19-17, A-130, and existing FICAM guidance and playbooks. Subject areas with intersecting scopes, such as delegations of authority, certificate issuance procedures, and internal controls are considered only to the extent that they relate to a digital autopen.

### Acknowledgments

This playbook reflects the contributions of the Delegated Digital Signature working group of the Federal Chief Information Security Officer Council Identity, Credential, and Access Management Subcommittee. The working group was co-chaired by the Internal Revenue Service and the General Services Administration. Contributing members include:
- Department of Agriculture
- Department of Health and Human Services
- Department of Homeland Security
- Department of State
- Department of Veterans Affairs
- General Services Administration
- Government Printing Office
- Internal Revenue Service
- National Archives and Records Administration

[Appendix B](#appendix-b-policy-recommendations) includes recommended policy and guidance updates identified by the working group.

## The Digital Autopen

Federal agencies must publish documents in the *Federal Register* for various reasons. Only federal employees with the proper authority may sign those documents. This authority is referred to as the Authorizing Sponsor in this document. When that Authorizing Sponsor is unavailable, they may authorize the use of a digital autopen to affix their signature to a *Federal Register* document. Multiple reasons exist why an authorizing sponsor may be unavailable.

1. No access to technology that can leverage a PIV card or digital signature certificate.
2. Travel situations outside of normal working hours that require Federal Register submission.
3. Efficiency when multiple documents must be signed.

The OFR outlines signing requirements in the [Document Drafting Handbook](https://www.archives.gov/files/federal-register/write/handbook/ddh.pdf){:target="_blank"}{:rel="noopener noreferrer"}. There are three main requirements.

1. The signer must be a federal employee with the authority to act for an agency. Laws or Executive Orders define which agency is the regulatory body, while an agency determines who has the authority to sign Federal Register documents.
2. The title in the signature block must be related to the authority to sign the document. It cannot include honorary titles or titles associated with a different agency role.
3. The signature block must match the signer's full name as it appears in the digital signature certificate subject name. See the OFR Document Drafting Handbook for accepted variations. The Personal Identity Verification (PIV) card is a primary means for digitally signing a document.

An agency may delegate the authority to electronically sign a document to someone with an official executive agency billet to sign a document, such as a Deputy Secretary or General Counsel. An agency may delegate a signature to an appropriate authority named in a Federal Register document (see Figure 1).

Figure 1. Named Delegation Example

