---
layout: page
collection: piv
title: PIV Identifiers
permalink: piv/identifiers/
sticky_nav: true
sidenav: piv
---

In applications including network domains, you will associate the PIV credential with your accounts.  This process is not unique to PIV credentials and usage; it is a general concept that occurs in many applications, including your personal email accounts, your bank accounts, or your favorite social media app.  

{% include alert-info.html content="Associating a credential with an account is called account linking." %}

_Identifiers_ are the values in credentials that are used for account linking.  We focus on the **PIV Authentication** certificate and identifiers in this section to help you understand the options and design and implement solutions for using PIV to authenticate to networks and applications. For more information on account linking, see [Account Linking](../network/account/){:target="_blank"}{:rel="noopener noreferrer"} .

The table below outlines identifiers available in the PIV Authentication certificate and design considerations for implementations.

| Identifiers              | Considerations |
| -------------            |----            |
| Subject      |  Unique for every person _within the same agency_; value does not change when a user receives a new, replaced, or updated PIV credential _within the same agency_. |
| Issuer and Subject      | Unique for every person; value does not change when a user receives a new, replaced, or updated PIV credential _within the same agency_. |
| Issuer and Serial Number   | Unique for every person and certificate; value changes when a user receives a new, replaced, or updated PIV credential. |
| Subject Key Identifier  | Unique for every person and certificate; value changes when a user receives a new, replaced, or updated PIV credential. |
| SHA-1 Hash of Public Key  | Value changes when a user receives a new, replaced, or updated PIV credential; commonly referred to as the _thumbprint_ of the certificate. |
| Federal Agency Smart Card Number (FASC-N)   | It is not recommended to use the FASC-N as an identifier; unique for every credential _only within the U.S. federal Executive Branch agencies_; no uniqueness for PIV credentials issued by Legislative or Judicial Branch agencies, state, local, tribal, territories, partners, or any credentials certified as PIV-Interoperable or _PIV-I_; value changes when a user receives a new, replaced, or updated PIV credential; legacy definition and usage supported building access control systems as outlined in [Technical Implementation Guidance: Smart Card Enabled Physical Access Control Systems)](https://www.idmanagement.gov/docs/pacs-tig-scepacs.pdf){:target="_blank"}{:rel="noopener noreferrer"} (PDF, 2005). |
| Card Universal Unique Identifier (UUID)      |   Unique for every person and credential; value changes when a user receives a new, replaced, or updated PIV credential; Card UUID value is only required to be present for new or replacement PIV credentials issued after August 2014; may also commonly be referred to as the Global Unique Identifier (GUID). |
| User Principal Name in _Subject Alternate Name_   |  Not required to be included in all PIV Authentication certificates; not recommended for use as an identifier to achieve full interoperability for networks or applications; commonly used for enterprise smart card logon / network authentication in _legacy_ implementations. |

For all items referencing an _agency_ in the table, you should consider the reference as the small organizational unit.  For example, a user who switches between one component in a large agency to another component may receive a new Subject Name when the user requires a replacement PIV credential.

{% include alert-warning.html heading="Organization Specific Identifiers" content="Multiple departments and agencies leverage a persistent, internal unique identifier. For example, the Department of Defense uses a unique 10-digit identifier called the Electronic Data Interchange Personal Identifier or EDIPI. The Department of Homeland Security and the Department of Health and Human Services leverage a similar persistent lifetime identifier for their identities. Note that these identifiers are unique within the systems that generate them. There is a risk of collision when leveraging these identifiers in external systems." %}
