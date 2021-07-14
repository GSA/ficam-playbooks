---
layout: page
collection: piv
title: Certificate Trust
permalink: piv/cert-trust/
sticky_sidenav: true
sidenav: piv

subnav:
  - text: Certificate Trust
    href: '#trust'
  - text: Certificate Chains
    href: '#certificate-chains'
  - text: Revocation
    href: '#revocation'
  - text: Download root and intermediate certificates
    href: '#download-root-and-intermediate-certificates'
---

One of the most common questions is "What are all these certificates and how do I configure my applications to use them?"  Answering this question involves explaining Trust, Certificate chains and Revocation.  

If you are looking for the root certificates, you can quickly jump to the end of the page for instructions!

## Trust
Identity certificates are issued and digitally signed by a _Certificate Authority_.  The _Certificate Authority_ that signed your PIV certificates is called an _**Intermediate** Certificate Authority_ because it was issued a certificate by another _Certificate Authority_.  This process of issuing and signing continues until there is one  _Certificate Authority_ that is called the _**Root** Certificate Authority_.

The full process of proving identity when issuing the certificates, auditing the certificate authorities, and the cryptographic protections of the digital signatures establish the basis of Trust for PIV credentials and certificates.

[![Example of an identity certificate with intermediate and root]({{site.baseurl}}/assets/piv/certificatechain_small.png){:style="float:center"}]({{site.baseurl}}/assets/piv/certificatechain_small.png){:target="_blank"}{:rel="noopener noreferrer"}

For the US Federal Government Executive branch agencies, there is one Root Certificate Authority named _Federal Common Policy Certificate Authority (COMMON)_, and dozens of Intermediate Certificate Authorities.  The US Federal Government has also established Trust with other Certificate Authorities which serve business communities, state and local government communities, and international government communities.

* [CLICK HERE: A graph of the federal public key infrastructure, including the business communities](../../fpki/tools/fpkigraph/){:target="_blank"}{:rel="noopener noreferrer"}

The participating Certificate Authorities and the policies, processes, and auditing is referred to as the [*Federal Public Key Infrastructure (FPKI)*](https://www.idmanagement.gov/community/twg/fpki-cas-audit-info/){:target="_blank"}{:rel="noopener noreferrer"}

## Certificate Chains
To digitally trust YOU and your PIV credential certificates, the workstations, servers, applications and network domains will be configured. Understanding and managing certificate chains are one of the methods to configure trust.

The certificate chain includes the Intermediate Certificate Authorities certificates and the Federal Common Policy Certificate Authority (COMMON) root certificate.

[![Example of a PIV certificate chain to Common]({{site.baseurl}}/assets/piv/pivcertificatechain_small.png){:style="float:center"}]({{site.baseurl}}/assets/piv/pivcertificatechain_small.png){:target="_blank"}{:rel="noopener noreferrer"}


{% include alert-info.html heading = "Federal PKI Person Root - COMMON" content="The Federal Common Policy Certificate Authority (COMMON) root certificate is included in Microsoft, Adobe and some Apple trust stores by default.  It is not included by default in Mozilla, java, all mobile device operating systems, or Linux based operating systems." %}

If you are an engineer working on implementing PIV authentication, you may need to download and install the root certificate (COMMON) for your workstations, servers, applications and network domains.

Many applications may require Intermediate Certificates to successfully trust ALL PIV credentials, and may not support the automatic retrieval of certificate chains.  You should consider the possible unintended consequences of installing intermediate certificates which _only_ represent intermediate certificate chains for your agency users.  You may want to be able to Trust all PIV credentials from agencies, and credentials from our trusted partners.  It is increasingly more common for users from other agencies or partners to _authenticate_ to your networks or applications, and this usage is the foundation of PIV to promote trust, interoperability, authentication, and efficiency across the US Federal Government.  

General recommendations for trust and certificate chain management include:

- COMMON should be used as the trusted root certificate authority
- Management of root and intermediate certificate authority certificates and distribution to network domains, workstations, servers and applications should be managed with group policy objects, secure automated distributions mechanisms, and enterprise policies and procedures to ensure updates are managed effectively.
- NIST published an [Information Technology Laboratory (ITL) bulletin](http://csrc.nist.gov/publications/nistbul/july-2012_itl-bulletin.pdf){:target="_blank"}{:rel="noopener noreferrer"} in July 2012 which includes general practices to consider.

Installation of the trusted root certificate and intermediate certificates is dependent upon operating systems and applications. Instructions for [downloading](#download-root-and-intermediate-certificates) are at the end of this page.

## Revocation
Revocation is the process and technology to identify a certificate as no longer valid - to tell computers and applications _"do not trust this certificate anymore."_

PIV credential certificates will be _revoked_ when a user terminates employment or a contract with an agency, is issued a new credential, is issued an updated PIV credential, or has a lost, stolen or damaged PIV credential.  The revocation of PIV credential certificates occurs with the PIV credential issuer and certificate authority.

There are two protocols available to verify if a PIV credential certificate has been revoked:

- Online Certificate Status Protocol (OCSP)
- Certificate Revocation Lists (CRLs)

Some implementations also validate whether the Intermediate Certificate Authority certificates have been _revoked_.  While a revocation of an Intermediate Certificate Authority certificate does not occur often, this is a safeguard in place and each Intermediate Certificate Authority and COMMON also publishes Certificate Revocation Lists for the certificates signed next in the chain.   

The table below outlines general information on each protocol, the certificate extension which contains the reference, and design considerations.

| Type | Certificate Extension | Protocol (Port) | Considerations|
| ----- | -------| -------| ------|
| OCSP | Authority Information Access | HTTP (80) | All PIV certificates have OCSP references and OCSP responder web services which are internet accessible and provided by the issuing certificate authority. Intermediate certificate authorities are **not** required to have OCSP available for the _intermediate_ certificates.|
| CRL  | CRL Distribution Point (CDP) | HTTP (80) | All PIV certificates have CRL references and CRLs files published to internet accessible web services by the issuing certificate authority.  All intermediate certificate authority certificates also have CRL references, files and internet accessible web services.  CRL files have an expiration time which varies between 6 hours to 18 hours. CRL file sizes distributed by issuing certificate authorities as of the date of this guide range from a few kilobytes to **over 30 megabytes (MB)**.

For a portion of your implementations such as network authentication, the _revocation_ checks will occur as part of the operating system or server native functionality.  Other implementations may want to consider services such as implementing Server Certificate Validation Protocol (SCVP).  These are advanced topics to consider and will be covered in other areas of guides soon.  

## Download root and intermediate certificates

The Federal Government recently deployed the Federal Common Policy CA (FCPCA) G2, a new Federal Public Key Infrastructure (FPKI) root Certification Authority (CA). As the existing Federal Common Policy CA reaches the end of its planned service life, FCPCA G2 will roll out incrementally and serve as the new trust anchor for the Federal PKI. Below, you’ll find important dates and steps for a successful operational transition to the FCPCA G2 trust anchor.

For instructions on how to download the new root and intermediate certificates, go to [the FPKI guide on the Federal Common Policy G2 Update](https://fpki.idmanagement.gov/common/obtain-and-verify/){:target="_blank"}{:rel="noopener noreferrer"}

#### Download any additional Intermediate Certificate Authority certificates

You can contact your agency's information security teams for help on additional intermediate certificates, or find the intermediate certificates by using information in your PIV certificates directly.

- View your PIV Authentication certificate. To review how to view your PIV Authentication certificate go to the [Details of a PIV Credential](../details){:target="_blank"}{:rel="noopener noreferrer"}
- In the **Authority Information Access (AIA)** extension, there is a URL (http://) which references a file with a .p7b or .p7c extension
- Download the file, open it, and view the intermediate certificate authority certificates
- Repeat the process using the AIA extension of the intermediate certificate authority certificates until the final reference finds an intermediate certificate authority certificate that is issued and signed by COMMON

Many products and implementations may automatically retrieve the intermediate certificates during a process called _certificate path building_ or _certificate path discovery_.   You will encounter varying implementations of the _certificate path discovery_ process based on differences in client operating systems, browsers, mobile devices, programming languages, and even applications directly. It can be challenging to understand all the options that impact your users and applications and we are seeking input and contributions to expand this information for you.     

We want to add more information to help you so check back often, or review the Issues posted and consider contributing!
