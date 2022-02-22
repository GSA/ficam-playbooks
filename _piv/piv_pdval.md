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

**Note:** The information in this playbook does not cover troubleshooting PDVal errors. Information about troubleshooting PDVal errors during smart card logon can be found in the Troubleshooting Windows Smart Card Logon with PIV-Authentication playbook [link to PIV Auth playbook when it's ready]

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

[text here]

### Choosing CA Certificates

[text here]

#### Public Key Identifiers

[text here]

## Certification Path Validation

[text here]

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

