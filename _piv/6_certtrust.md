---
layout: page
collection: piv
title: Certificate Trust
permalink: piv/cert-trust/
sticky_sidenav: true
sidenav: piv

subnav:
  - text: Trust
    href: '#trust'
  - text: Certificate Chains
    href: '#certificate-chains'
  - text: Revocation
    href: '#revocation'
  - text: Download Root and Intermediate Certificates
    href: '#download-root-and-intermediate-certificates'
---

Some of the most common questions about PIV are "What are all these certificates, and how do I configure my applications to use them?"  Answering these questions involves explaining trust, certificate chains, and revocation.  

If you are looking for the root certificates, you can quickly [jump to the end of the page](#download-root-and-intermediate-certificates) for instructions.

## Trust
Identity certificates are issued and digitally signed by a _certification authority (CA)_.  The _CA_ that signed your PIV certificates is called an _**intermediate** CA_ because it was issued a certificate by another _CA_.  This process of issuing and signing continues until there is one  _CA_ that is called the _**root** CA_.

The full process of proving identity when issuing the certificates, auditing the certification authorities, and the cryptographic protections of the digital signatures establish the basis of trust for PIV credentials and certificates.

<img src="{{site.baseurl}}/assets/piv/certificatechain_small.png" alt="Example of an identity certificate with intermediate and root." width="506" height="269">

For the federal government Executive Branch agencies, there is one root CA named _Federal Common Policy Certificate Authority G2 (FCPCAG2 or COMMON)_ and there are dozens of intermediate CAs.  The federal government has also established trust with other CAs that serve business communities, state and local government communities, and international government communities.

The participating CAs are subject to policies, processes, and auditing collectively referred to as the [*Federal Public Key Infrastructure (FPKI)*](https://www.idmanagement.gov/governance/fpkiaudit/){:target="_blank"}{:rel="noopener noreferrer"}

The [FPKI Graph]({{site.baseurl}}/fpki/tools/fpkigraph/){:target="_blank"}{:rel="noopener noreferrer"} is an interactive chart of the Federal Public Key Infrastructure CAs, including cross-certified business communities.


## Certificate Chains
To digitally trust YOU and your PIV credential certificates, the workstations, servers, applications, and network domains will be configured. Understanding and managing certificate chains are one of the methods to configure trust.

The certificate chain includes the intermediate CA certificates and the Federal Common Policy Certification Authority G2 (COMMON) root certificate.

<img src="{{site.baseurl}}/assets/piv/pivcertificatechain_small.png" alt="Example of a PIV certificate chain to Common." width="506" height="268">

{% include alert-info.html heading = "Federal PKI Person Root - COMMON" content="The Federal Common Policy Certification Authority G2 (COMMON) root certificate is included in Adobe trust stores by default.  It is not included by default in Microsoft, Apple, Mozilla, Java, all mobile device operating systems, or Linux based operating systems." %}

If you are an engineer working on implementing PIV authentication, you may need to download and install the root certificate (COMMON) for your workstations, servers, applications and network domains.

Many applications may require intermediate certificates to successfully trust ALL PIV credentials and may not support the automatic retrieval of certificate chains.  You should consider the possible unintended consequences of installing intermediate certificates which _only_ represent intermediate certificate chains for your agency users.  You may want to be able to trust all PIV credentials from agencies and credentials from our trusted partners.  It is increasingly more common for users from other agencies or partners to _authenticate_ to your networks or applications; this usage is the foundation of PIV to promote trust, interoperability, authentication, and efficiency across the U.S. federal government.  

General recommendations for trust and certificate chain management include:

- COMMON should be used as the trusted root CA.
- Management of root and intermediate CA certificates and distribution to network domains, workstations, servers and applications should be managed with group policy objects, secure automated distributions mechanisms, and enterprise policies and procedures to ensure updates are managed effectively.
- NIST published an [Information Technology Laboratory (ITL) bulletin](http://csrc.nist.gov/publications/nistbul/july-2012_itl-bulletin.pdf){:target="_blank"}{:rel="noopener noreferrer"} in July 2012 which includes general practices to consider.

Installation of the trusted root certificate and intermediate certificates is dependent upon operating systems and applications. Instructions for [downloading certificates](#download-root-and-intermediate-certificates) are at the end of this page.

## Revocation
Revocation is the process and technology used to identify a certificate as no longer valid—to tell computers and applications _"do not trust this certificate anymore."_

PIV credential certificates will be _revoked_ when a user terminates employment or a contract with an agency, is issued a new credential, is issued an updated PIV credential, or has a lost, stolen, or damaged PIV credential.  The revocation of PIV credential certificates occurs with the PIV credential issuer and CA.

There are two protocols available to verify if a PIV credential certificate has been revoked:

- Online Certificate Status Protocol (OCSP)
- Certificate Revocation Lists (CRLs)

Some implementations also validate whether the intermediate CA certificates have been _revoked_.  While revocation of an intermediate CA certificate does not occur often, it is a safeguard in place and each intermediate CA and COMMON also publishes CRLs for the certificates signed next in the chain.   

The table below outlines general information on each protocol, the certificate extension that contains the reference, and design considerations.

| Type | Certificate Extension | Protocol (Port) | Considerations|
| ----- | -------| -------| ------|
| OCSP | Authority Information Access | HTTP (80) | All PIV certificates have OCSP references and OCSP responder web services which are Internet accessible and provided by the issuing CA. Intermediate CAs are **not** required to have OCSP available for the _intermediate_ certificates.|
| CRL  | CRL Distribution Point (CDP) | HTTP (80) | All PIV certificates have CRL references and CRLs files published to Internet accessible web services by the issuing CA.  All intermediate CA certificates also have CRL references, files, and Internet accessible web services.  CRL files have an expiration time that varies between 6 to 18 hours. CRL file sizes distributed by issuing CAs as of the date of this guide range from a few kilobytes to **more than 30 megabytes (MB)**.

For a portion of your implementations such as network authentication, the _revocation_ checks will occur as part of the operating system or server native functionality.  Other implementations may want to consider services such as implementing Server Certificate Validation Protocol (SCVP).  These are advanced topics to consider and will be covered in other areas of the guides soon.  

## Download Root and Intermediate Certificates

The federal government recently deployed the Federal Common Policy CA G2 (FCPCAG2), a new Federal Public Key Infrastructure (FPKI) root CA. As the existing Federal Common Policy CA reaches the end of its planned service life, FCPCAG2 will roll out incrementally and serve as the new trust anchor for the Federal PKI. Below, you’ll find important dates and steps for a successful operational transition to the FCPCAG2 trust anchor.

For instructions on how to download the new root and intermediate certificates, go to [the FPKI guide on the Federal Common Policy G2 Update](https://fpki.idmanagement.gov/common/obtain-and-verify/){:target="_blank"}{:rel="noopener noreferrer"}

#### Download Any Additional Intermediate Certification Authority Certificates

You can contact your agency's information security teams for help with additional intermediate certificates, or you can find the intermediate certificates by using information in your PIV certificates directly.

- View your PIV Authentication certificate. To review how to view your PIV Authentication certificate, go to the [PIV Details](../details){:target="_blank"}{:rel="noopener noreferrer"}
- In the **Authority Information Access (AIA)** extension, there is a URL (http://) that references a file with a .p7b or .p7c extension.
- Download the file, open it, and view the intermediate CA certificates.
- Repeat the process using the AIA extension of the intermediate CA certificates until the final reference finds an intermediate CA certificate that is issued and signed by COMMON.

Many products and implementations may automatically retrieve the intermediate certificates during a process called _certificate path building_ or _certificate path discovery_.   You will encounter varying implementations of the _certificate path discovery_ process based on differences in client operating systems, browsers, mobile devices, programming languages, and even applications directly. It can be challenging to understand all the options that impact your users and applications; we are seeking input and contributions to expand this information for you.     

We want to add more information to help you, so check back often or review the Issues posted and consider contributing!
