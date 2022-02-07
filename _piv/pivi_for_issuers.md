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

(text here)

|                  | Technical Requirements | PIV | PIV-Interoperable|
|------------------|--------------------------------------|:------------:|:----------------------:|
| **Trust**      | Identity Assurance:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● Level of Assurance 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● Identity Assurance Level 3 (draft NIST SP 800-63-3) | ● | ● |
|                        | Authenticator Assurance:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● Level of Assurance 4<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● Authenticator Assurance Level 3 (draft NIST SP 800-63-3) | ● | ● |
|                        | Suitability Assurance:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;● Favorably adjudicated National Agency Check with Inquiries (minimum) or other Tier 1 investigation | ● |    |
|                        | PIV policy object identifier on PIV Authentication Certificates | ● |    |
|                        | PIV-I equivalent policy object identifier on PIV-I Authentication Certificates |    | ● |
|                        | PIV Content Signing object signing certificate | ● |    |
|                        | PIV-I Content Signing equivalent object signing certificate |    | ● |
|                        | Card stock certified | ● | ● |
|                        | PIV Application Identifier (AID) | ● | ● |
|                        | Command edge and NIST SP 800-85 conformant | ● | ● |
| **Credential Edge** | NIST SP 800-73-4 conformant GUID present in the CHUID | ● | ● |
|                        | RFC 4122 conformant UUID required in the GUID data element of the CHUID | ● | ● |
|                        | RFC 4122 conformant UUID present in the Authentication Certificates | ● | ● |





# 1. Introduction
## 1.1 Background

(text here)

## 1.2 Scope

(text here)

## 1.3 Document Objectives

(text here)

## 1.4 Assumptions

(text here)

# 2. Minimum Credential Requirements
## 2.1 Common Terminology for Identity Credentials

(text here)

## 2.2 Trusted Identity

(text here)

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