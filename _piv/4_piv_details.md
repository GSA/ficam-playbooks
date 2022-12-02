---
layout: page
collection: piv
title: PIV Details
permalink: piv/details/
sticky_sidenav: true
sidenav: piv

subnav:
    - text: View Your PIV Credential Certificates
      href: '#view-your-piv-credential-certificates'
    - text: Export PIV Certificates
      href: '#export-piv-certificates'
    - text: Understand PIV Certificates
      href: '#understand-piv-certificates'
---

You can use these simple methods to view, export, and understand the information stored on a PIV credential.

## View Your PIV Credential Certificates

Almost **all** of the methods for using your PIV credential for networks, applications, digital signatures, and encryption involve the certificates and key pairs stored on your PIV credential.  There are also scenarios where additional information (such as biometrics) is also accessed and used. 

To view your certificate information:

-   Insert your PIV credential into your card reader.
-   Choose an option from the table below and follow the steps.

| Operating System     | Module   | Steps |
| -------------             |----|----|
| Microsoft   | Internet Explorer  | Open _Internet Explorer Browser_ -> _Tools Wheel_ or Alt+X) -> _Internet Options_ -> _Content Tab_ -> _Certificates Button_ -> _Personal Tab_  |
| Microsoft       | Microsoft Management Console (MMC) and Certificate Snap-in  |  Open _Microsoft Management Console_ -> _File_ -> _Add/Remove Snap-In_ -> _Certificates Snap-in_ -> _Add_ -> _My user account_ -> _Finish_ -> Expand _Certificates - Current User_ -> _Personal_ -> _Certificates_   |
| Any   | Chrome Browser  | Open _Chrome Browser_ -> _Settings_ -> _Show Advanced Settings_ -> _Manage Certificates_ (_Manage HTTPS/SSL Certificates and Settings_)  -> _Personal_ tab  |
| Any   | Firefox Browser  | Open _Firefox Browser_ -> _Settings_ wheel -> _Privacy & Security_ -> _Security_ -> _Certificates_ > _View Certificates_ button -> _Certificates Manager_ -> _Your Certificates Tab_
| macOS X   | Keychain  | Open _Applications_ -> _Utilities_ -> _Keychain Access_ -> Select _Login_ -> _Categories_ -> _My Certificates_  |

{% include alert-info.html heading = "View" content="You may see many certificates.  To open and view the certificate details, double-click on any certificate." %}

## Export PIV Certificates
We won’t always use graphical user interfaces to view the PIV credential certificates. Throughout the PIV and the Federal PKI (FPKI) Guides, we're continuing to add useful procedures for network engineers and examples of code, tools, and common _command line_ options for viewing and troubleshooting configurations.  (**Note:** These examples may use files representing _public_ certificates.)

{% include alert-info.html heading = "Export" content="Look for an Export button and save the file as DER or PEM-encoded, with a file extension of cer (.cer)." %}

{% include alert-warning.html heading = "Keys are safe!" content="Don't worry; the public certificates are public. The private keys are always stored safely on your PIV credential and can never be exported. " %}

## Understand PIV Certificates

Viewing the certificate information on your PIV credential may be interesting if you are a general user.  You **must** understand certificate information as a program manager or engineer developing applications and designing solutions for using PIV credentials.

Within the U.S. federal government, the certificate and PIV credential information is governed by standards, policies, and implementation-specific choices (options) across all agency credential providers.

Typically, there are four certificates and four key pairs on a PIV credential.  However, one pair (i.e., one certificate and one key pair) is *ALWAYS* on every PIV credential and three pairs (i.e., three certificates and three key pairs) are *SOMETIMES* on a PIV credential.  You can review the [PIV Overview](../basics/) to view the four pairs and purposes.

The table below outlines the general information for the PIV credential certificates, certificate extensions, and design considerations. 

{% include alert-info.html heading = "6 Years" content="PIV credentials and certificates have changed over time due to updates in standards.  Since users may have credentials for up to 6 years and there are both optional and mandatory elements, the information presented is what is valid for ALL PIV credentials and certificates currently in use. (Although credentials are valid for 6 years, the certificates contained on a credential are valid for only 3 years, with the exception of the content signer.)" %}

| Certificate              | Required  | Key Usage | Extended Key Usage  | Subject Alternative Name | Design Considerations |
| -------------            |:----:      |:----:               |:----:               |:----:|  ----|
| PIV Authentication | Always | Digital Signature | Client Authentication | otherName = FASC-N;<br> uniformResourceIdentifier = UUID;<br>Principal Name = _prefix_@_suffix_  | Principal Name values are **not** required by policy to be present in all Subject Alternative Name extensions. The Card UUID may also commonly be referred to as the Global Unique Identifier (GUID). |
| Card Authentication | Always | Digital Signature | id-PIV-cardAuth |  Name = FASC-N; <br>uniformResourceIdentifier = UUID|   Card Authentication must be included in new and replacement PIV credentials issued after August 2014; it is not expected that **all** PIV credentials will have Card Authentication certificates until September 2019. The Card UUID may also commonly be referred to as the GUID. |
| Digital Signature | Sometimes | Digital Signature, Non-Repudiation | Specific EKUs are required for certificates issued after June 2019 | rfc822name = email address | Email address is **not** required by policy. Email address may be multivalued attributes and include email aliases. |
| Encryption |Sometimes | Key Encipherment | Specific EKUs are required for certificates issued after June 2019 | rfc822name = email address | Email address is **not** required by policy. Encryption certificates that represent available, retired encryption key pairs may exist, depending on the PIV issuer. |
| PIV Content Signer  | Always  | Digital Signature  | id-PIV-content-signing  | N/A  | The PIV content signer ensures the integrity of the digital information stored on the card. Physical Access Control Systems (PACS) are the primary relying party for these certificates. This certificate is unavailable in most logical trust stores, but users can leverage the [Card Conformance Tool (CCT](https://playbooks.idmanagement.gov/fpki/tools/cct/) if they would like to extract and view the PIV content signing certificate.  |

Additional useful information:

-   All key pairs for users are 2048-bit (RSA) keys.
-   All certificates issued and certified as _PIV_ are SHA-256 signed.
-   If you are working with _Common Access Cards_, you may still encounter SHA-1-signed certificates and might _not_ see a Card Authentication certificate.
-   There has been testing in some infrastructures to migrate to Elliptic Curve Cryptography (ECC), but there are no ECC certificates for users in production as of the date of this guide.
-   There has been testing in some infrastructures to migrate to 3072-bit (RSA) certificates, but there are no 3072-bit certificates for users in production as of the date of this guide.

In-depth details on the certificate profiles are contained in the current and historical Federal Public Key Infrastructure (FPKI) policy documents. The most recent policy and certificate profile documents may be found on IDManagement.gov's [FPKI Policy and Compliance Audit](https://www.idmanagement.gov/governance/fpkiaudit/){:target="_blank"}{:rel="noopener noreferrer"} page.

