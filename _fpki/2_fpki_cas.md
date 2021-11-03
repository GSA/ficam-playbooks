---
layout: page
collection: fpki
title: FPKI Certification Authorities Overview
permalink: /fpki/ca/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: Federal Common Policy Certification Authority
    href: '#federal-common-policy-certification-authority'
  - text: Federal Bridge Certification Authority
    href: '#federal-bridge-certification-authority'
  - text: All Federal PKI Certification Authorities
    href: '#all-federal-pki-certification-authorities'
  - text: Federal Common and Federal Bridge Certificate Details
    href: ../certsandcrls/
  - text: PIV CAs and Agencies
    href: ../pivcas-and-agencies/
---

A **_certification authority_** is a system that issues digital certificates. These digital certificates are based on _cryptography_ and follow the X.509 standards defined for information security.

The Federal PKI (FPKI) is a network of certification authorities (CAs) that are either _root_, _intermediate_, or _issuing_ CAs.

Any CA in the FPKI may be referred to as a _Federal PKI CA_. The two highest level CAs in the FPKI hierarchy are the **_FPKI Trust Infrastructure CAs_**, which are operated and managed by the [Federal PKI Management Authority (FPKIMA)](https://www.idmanagement.gov/governance/ficam/#federal-public-key-infrastructure-management-authority){:target="_blank"}{:rel="noopener noreferrer"} Program Office:

- [Federal Common Policy Certification Authority](#federal-common-policy-certification-authority)
- [Federal Bridge Certification Authority](#federal-bridge-certification-authority)
- [All Federal PKI Certification Authorities](#all-federal-pki-certification-authorities)

COMMON serves as the _root_ and _trust anchor_ for the _intermediate_ and _issuing_ CAs operated by federal government Executive Branch agencies.

{% include alert-info.html content="<strong>Public trust for websites</strong><br>A new effort is in the planning stages to establish another federal government root and issuing CAs dedicated to Public Trust Transport Layer Security (TLS) device certificates. Follow or contribute to the development of the federal government's new certificate policy for this Public Trust effort at https://github.com/uspki/policies" %}

### Federal Common Policy Certification Authority

The _Federal Common Policy CA_ may be referred to as the _FCPCAG2_, or as _COMMON_ in documents. As the FPKI root and trust anchor for the federal government, the FCPCAG2 supports government person trust and a small number of agency intranet enterprise devices, including [Personal Identity Verification (PIV) credentials](../../piv#what-is-piv){:target="_blank"}. The FCPCA's design enables any certificate issued by any FPKI CA to validate its certificate path to a single root CA.

A few commercial vendors include the FCPCAG2 root certificate in the commercial-off-the-shelf (COTS) products' [trust stores](../trust-stores/). This enables federal government systems to trust person and enterprise device certificates issued by FPKI CAs. It is possible to add the FCPCAG2 root certificate to trust stores for _government-managed_ devices and servers, if it's not available by default.

{% include alert-warning.html content="The FCPCAG2 root certificate is included in the trust stores for some platforms such as Adobe. Other platforms, such as Microsoft, Mozilla, and Apple, do not include the FCPCA by default. " %}

### Federal Bridge Certification Authority

<a href="../../assets/fpki/intro_fbca-logo.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/fpki/intro_fbca-logo.png" width="180" align="left" alt="FPKI Federal Bridge Logo"></a>

The current Federal Bridge Certification Authority (FBCA) is the _**Federal Bridge CA G4**_.

The FBCA is a PKI bridge or link between the FCPCA and other CAs that comprise the FPKI network and that may operate under comparable but _different_ certificate policies. The FBCA provides a means to map these certificate policies and CAs and allow certificates to validate to the FCPCA root certificate.
  
The CAs with certificates signed by the Federal Bridge CA G4 are _cross-certified_. These CAs have established a trust relationship with the FPKI and are audited annually for conformance to the certificate policies. This cross-certification process has extended the reach of the FPKI well beyond the boundaries of the federal government.

### All Federal PKI Certification Authorities

<a href="../../assets/fpki/intro_participatingCAsV3.png" target="_blank" rel="noopener noreferrer"><img src="../../assets/fpki/intro_participatingCAsV3.png" width="200" align="left" alt="FPKI Participating CAs"></a>

A CA that is part of the FPKI is called a _participating certification authority_. 

For historical records, we might _label_ or identify CA systems using a category that shows _when_ the system was established and for what types of _communities_ it is or was used. 

We realize all the acronyms and labels may be confusing and welcome your input to help us improve, add information over time, and simplify where needed. 


|**Certification Authority Category**|**Description**|
|-----------|---------------|
| PKI Shared Service Provider (SSP) Certification Authorities | An SSP CA is *subordinate* to the FCPCAG2.  Any certificate that an SSP CA creates, signs, and issues to people or devices is in the FCPCA _trust chain_. An SSP must adhere to strict federal IT security standards and requirements.  The SSPs are granted a FISMA Authority to Operate (ATO), undergo continuous monitoring, and are contracted by the federal government to issue certificates to federal employees and contractors as well as devices that are deployed in federal agency networks. |
| Private Sector Certification Authorities | A private sector CA that is cross-certified has shown a valid need to conduct business or provide PKI services to the federal government. |
| Other Government Certification Authorities | These CAs are managed and operated by state, local, tribal, territorial, or international governments. |
| Bridge Certification Authorities | Bridge CAs connect member PKIs and are designed to enable interoperability between different PKIs operating under their own certificate policies. A bridge CA is not a _root_. |
| Federal Agency Legacy | Prior to 2004, some agencies had already deployed and invested in their own PKI and CAs. Some of these agencies opted out of migrating to the SSP Program and continued to manage their existing infrastructures. These federal agencies legacy operate one or more CAs that are cross-certified with a Federal PKI Trust Infrastructure CA.|
