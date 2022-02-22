---
layout: page
collection: piv
title: Certification Path Discovery and Validation
permalink: piv/pdval/
sticky_sidenav: true
sidenav: piv

subnav:
    - text: Introduction
      href: '#introduction'
    - text: What Is a Trust Anchor?
      href: '#what-is-a-trust-anchor'
    - text: What Is Path Discovery and Validation?
      href: '#what-is-path-discovery-and-validation'
    - text: What Is a Certification Path?
      href: '#what-is-a-certification-path'
    - text: Certification Path Discovery
      href: '#certification-path-discovery'
    - text: Certification Path Validation
      href: '#certification-path-validation'
    - text: References
      href: '#references'
---

## Introduction

When federal employees use their PIV cards to authenticate (e.g., gain access to a website or a physical door into a facility) or digitally sign a document, they are using one of potentially three certificates on their PIV card.  The software interacting with the PIV card and certificate must verify that the X.509 (the technical standard that defines the data structure of certificates used Internet-wide) digital certificate is valid and trusted to a trust anchor. This playbook provides an overview of this verification process in the context of Federal PKI.

If you have heard terms like PDVal, trust paths, certificate paths, trust fabric, trust anchors, and Microsoft CAPI to name a few, you are in the right place.

## What Is a Trust Anchor?

Most simply, a trust anchor is a trusted certification authority (CA). These may be commonly called trust root, trusted CA, or root CA. Everything in PKI traces its trust back to a trust anchor.

The trust anchor operated by Federal PKI is the **Federal Common Policy CA.** All PIV certificates should have a valid certification path to the Federal Common Policy CA. For more information, see the guidance provided in the [Federal Common Policy CA Update](https://playbooks.idmanagement.gov/fpki/common/){:target="_blank"}{:rel="noopener noreferrer"}. A common misconception is that the Federal Bridge is the root of trust for the community.  Keep reading to understand why that is not the case.

## What Is Path Discovery and Validation?

Commonly referred to as certificate validation, **Certification Path Discovery and Validation (PDVal)** is a procedure used to determine whether there is a way to associate a certificate to a trust anchor and confirm that the certificate is valid for use.

PDVal should occur every time a certificate is used. Some common PIV card use cases include:
- Logging onto a workstation
- Authenticating to an application using a web browser.
- Verifying a digital signature (for example, signed email or digitally signed documents)
- Encrypting data for others (for example, encrypted email)
- Accessing a building or an office

PDVal is a two-step process:
1. **Certification Path Discovery:** Find a certification path to a trust anchor. 
2. **Certification Path Validation:** Confirms that the certification path is good. 

**Note:** The information in this playbook does not cover troubleshooting PDVal errors. Information about troubleshooting PDVal errors during smart card logon can be found in the Troubleshooting Windows Smart Card Logon with PIV-Authentication playbook [LINK TO PIV AUTH TROUBLESHOOTING PLAYBOOK WHEN IT'S READY]

**Note:** This document describes the PDVal process as documented in standards. Individual vendor implementations may not support all the capabilities described in this playbook, and the details of individual implementations may vary.

### The Federal PKI

The Federal PKI (FPKI) includes a large number of CAs. They are managed by federal agencies, commercial providers, foreign allies, or private enterprises that issue certificates according to federal policy. The FPKI also includes what are known as bridge CAs that enable two-way trust. The bridge CA operated by FPKI is the Federal Bridge CA. 

The image below illustrates the FPKI with Federal Common Policy CA G2 as the trust anchor.

[![An image showing the FPKI with Federal Common Policy CA G2 as the trust anchor.]({{site.baseurl}}/assets/piv/pdval-trust-anchor.png)]({{site.baseurl}}/assets/piv/pdval-trust-anchor.png){:target="_blank"}{:rel="noopener noreferrer"}

Operating systems and many digital certificate supporting software packages come with a predefined **static** list of trust anchors called a **certificate trust list**. The trust lists can usually be further modified to add or remove specific trust anchors. This resulting list could include multiple trust anchors that are directly or indirectly connected to Federal PKI. These lists must be manually maintained over time.

For example, the CertiPath Bridge CA can be seen in the above image. Several members of the Aerospace and Defense community have two-way (i.e., the bridge and the member CA have chosen to trust each other and have issued each other technical evidence of that trust for anyone to see) cross-certifications with that bridge that enable them to act as a peer and rely on their own trust anchor for interactions with Federal PKI. Examples include Raytheon Technologies, Northrop Grumman, and Boeing.

GSA’s FPKI site contains the complete [graphical FPKI CA ecosystem](https://playbooks.idmanagement.gov/fpki/tools/fpkigraph/){:target="_blank"}{:rel="noopener noreferrer"} displaying the relationships between the CAs. The graph depicts how each CA links to each other, through cross-certificates, subordinate certificates, or bridge CAs. 

**Fun Fact:** Microsoft Windows includes trust anchors that were previously connected to the FPKI via the Certipath Bridge CA. The Netherlands Ministry of Defense was connected until November 2015 and Carillon Information Security was connected until February 2020.

## What Is a Certification Path?

Sometimes referred to as a certificate chain or a trust path, a certification path is the sequence of unique CA certificates between a trust anchor and a certificate issued to a person or device. Starting with the trust anchor, each subsequent CA certificate in the sequence was created and digitally signed (“issued”) by the preceding CA’s key. By verifying the digital signatures on each certificate in the sequence, trust is conveyed from the trust anchor to the person or device certificate.

Two valid certification paths for the same PIV authentication certificate are illustrated below.

[![An example certification path from the Federal Common Policy CA G2.]({{site.baseurl}}/assets/piv/pdval-example-cert-path-1.png)]({{site.baseurl}}/assets/piv/pdval-example-cert-path-1.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Example Certification Path 1 - from Federal Common Policy CA G2</b></p>

[![An example certification path from the Raytheon Technologies Root CA.]({{site.baseurl}}/assets/piv/pdval-example-cert-path-2.png)]({{site.baseurl}}/assets/piv/pdval-example-cert-path-2.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Example Certification Path 2 - from Raytheon Technologies Root CA</b></p>

Both certification paths are valid for the same PIV authentication certificate (”(Affiliate)” in the images), but they start with different trust anchors. The configuration difference between the two example paths is only which trust anchor was installed.

A variety of factors can influence which certification path is used on a system, including:
- Which trust anchor CAs (Also known as trust roots or trusted CAs) are installed
- Locally cached CA certificates
- Dates the CA certificates were issued and/or expire
- The content of the CA certificates

The most important factor is the trust anchors. By limiting which trust anchors are installed, only certification paths to those trust anchors can be used on the system. Systems that are for agency use should only find certification paths to the Federal Common Policy CA for PIV certificates. If a certification path to another trust anchor is discovered, the trust anchor can be removed from the system to ensure that all certification paths validate to the Federal Common Policy CA.

**Critical Note:** If certification paths from your PIV certificates do not begin with the Federal Common Policy CA G2, follow the guidance found in [Distribute the certificate to operating systems](https://playbooks.idmanagement.gov/fpki/common/distribute-os/){:target="_blank"}{:rel="noopener noreferrer"} to install the CA in the correct location. 

## Certification Path Discovery

The first step of PDVal is finding a certification path for the certificate that needs to be verified.  The process for finding the path is called path discovery or path development.

In simple cases like verifying your own agency's PIV card, this is a straightforward procedure involving only one or two CA certificates (see the Example Certification Path 1 image in the previous section) In other situations, such as validating a PIV-I certificate, the procedure can involve many CAs and significantly more challenging path discovery requirements.

[![An example PIV-I certification path.]({{site.baseurl}}/assets/piv/pdval-pivi-cert-path.png)]({{site.baseurl}}/assets/piv/pdval-pivi-cert-path.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>PIV-I Certification Path</b></p>

Software providers use different path discovery methods. Describing all of them is beyond the scope of this playbook, but the simple path discovery algorithm below illustrates the concept. 

When a certificate must be verified, software may repeat the following path discovery procedure: 

[![A simple path discovery algorithm.]({{site.baseurl}}/assets/piv/pdval-path-discovery-algorithm.png)]({{site.baseurl}}/assets/piv/pdval-path-discovery-algorithm.png){:target="_blank"}{:rel="noopener noreferrer"}

If the procedure is unable to obtain the next issuing CA certificate, the process fails.

### Finding CA Certificates

For simple cases, the necessary CA certificates are often administratively installed or are cached locally by the certificate consuming software or the operating system. In more complicated situations such as verifying a PIV certificate from another agency or a PIV-I card from a commercial vendor, software must actively retrieve the CA certificates needed to discover a complete certification path. Certificates have a field called the Authority Information Access (AIA) extension which enables the path discovery implementation to do exactly that. 

In the FPKI, all certificates are required to contain an AIA with an Internet-accessible URL inside. The URL usually points to a “p7c” file that contains one or more issuing CA certificates.

[![A screenshot showing Authority Information Access in a certificate issued by the Federal Bridge CA.]({{site.baseurl}}/assets/piv/pdval-aia-in-cert.png.png)]({{site.baseurl}}/assets/piv/pdval-aia-in-cert.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>AIA in a Certificate Issued by the Federal Bridge CA</b></p>

Path discovery follows the AIA URLs, one after the other from each certificate in sequence, until it finds a certificate issued by a trust anchor in the certificate trust list.  The figure below shows the discovery of a single correct path.  In practice though, there could be many false paths evaluated and potentially even more than one valid path discovered. The path processing software then must choose which path to use.

**Fun Fact:** The algorithm to decide which correct path to choose has been a source of much debate in the PDVal community for more than two decades.

[![A diagram showing the discovery of a single correct path.]({{site.baseurl}}/assets/piv/pdval-path-discovery.png)]({{site.baseurl}}/assets/piv/pdval-path-discovery.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Illustrative Path Discovery</b></p>

### Choosing CA Certificates

As mentioned in the previous section, the AIA URLs may point to files that contain more than one CA certificate, each of which could be valid entries in a certification path to your desired trust anchor. In the diagram below, the AIA URL for the Bridge CA contains three valid CA certificates. 

[![A diagram showing path discovery in a bridge PKI environment.]({{site.baseurl}}/assets/piv/pdval-path-discovery-bridge-pki.png)]({{site.baseurl}}/assets/piv/pdval-path-discovery-bridge-pki.png){:target="_blank"}{:rel="noopener noreferrer"}

<p align="center"><b>Illustrative Path Discovery in a Bridge PKI Environment</b></p>

As an example, assume that the path discovery software is attempting to find a certification path from an end user on the left to the trust anchor on the right. Said another way, we trust the anchor on the right but have been presented with the user’s credential on the left and need to see if there is any means to trust it.  When the process retrieves the AIA URL for the Bridge, it must select the CA certificate issued to the Bridge by CA C. Path discovery software that fails to select the correct certificate or is incapable of backtracking to attempt other choices may fail to find a valid certification path or end the search in an unexpected location, such as the far side of the Federal Bridge.

**Fun Fact:** Yes, we wanted to say _a bridge too far_ when we wrote that.

**Ah-Ha Fact:** Bridges create transitive trust.  You may recall the transitive property from Algebra.  If A = B and B = C, then A = C.  That is exactly what is going on here.  The end user’s credential above is ultimately able to be trusted because we found a means to trust its issuer and we did not directly trust that issuer already.  The means to do that was established through the transitive property.  Without constraints, transitive trust could theoretically be built indefinitely.

**A-Ha Fact:** The song _Take On Me_ was recorded and failed to chart three times before the addition of the ground-breaking video and a fourth recording saw it chart to number 1. If this had been a **Take on Me note**, it would have been E<sub>5</sub>.

Fortunately, beyond the more obvious matching of certificate names in the certification path, certificates provide useful information for guiding path discovery, the most important of which are public key identifiers. 

#### Public Key Identifiers

You can think of these identifiers as unique nicknames for the keys in the certificates. Certificates usually contain two public key identifiers:
- **Subject Key Identifier (SKID):**  Nickname for the key inside this certificate
- **Authority Key Identifier (AKID):** Nickname for the key inside my issuing CA’s certificate

When a CA issues a certificate, it populates its SKID value into the AKID value of the issued certificate. This bread crumb or chaining trail allows for path discovery to choose the CA certificate with the correct key when discovering the certification path.

This mechanism becomes essential when CAs get a new key, a process called **key rollover**. In the image below, CA 1 has had a prior key rollover, resulting in two different certificates issued to CA 2. In this case, the path discovery software can match the authority key identifier in CA 2 to the subject key identifier in the CA 1 certificate to determine which certificate to use. 

[![A diagram illustrating prior key rollover.]({{site.baseurl}}/assets/piv/pdval-prior-key-rollover.png)]({{site.baseurl}}/assets/piv/pdval-prior-key-rollover.png){:target="_blank"}{:rel="noopener noreferrer"}

## Certification Path Validation

With a path discovered, now we need to see if it is valid.

Certification path validation is the second step of PDVal where the process determines if a discovered certification path is valid. The FPKI seeks to conform to RFC 5280, so any certification path validation software that fully implements RFC 5280 path validation requirements should interoperate with all aspects of FPKI.

For each certificate in the certification path, basic checks confirm the following about the certificate:
- It is not expired
- The signature is verified
- The issuer name matches the CA subject name
- It contains required fields
- It is not revoked

Then the complete certification path is checked for the correct  
- Certificate policies 
- Certification path constraints

If all these checks pass, the certification path is considered valid. The sections below provide additional details on these steps.
It is worth noting that some aspects of path validation may be successfully incorporated with the path discovery process. Although these techniques are not discussed in this playbook, they are discussed in detail in [RFC 4158](https://www.rfc-editor.org/rfc/rfc4158.html){:target="_blank"}{:rel="noopener noreferrer"}.

**Note:** Certification path validation is a process defined in ITU-T X.509.  RFC 5280 is a profile of X.509 and contains a subset of the functionality deemed necessary for interoperability in an Internet-connected environment.  X.509 should be consulted in any case where RFC 5280 content is in question, unclear, or silent. This playbook aims to provide readers with a summary of some core certification path validation requirements, it should not be considered authoritative.

### Basic Certificate Checks

[text here]

#### Validity Period

[text here]

#### Signature Verification

[text here]

#### Name Matching

[text here]

#### Revocation Checking

[text here]

### Certificate Policies

[text here]

#### Policy Mapping

[text here]

### Certification Path Constraints

[text here]

## References

[text here]

