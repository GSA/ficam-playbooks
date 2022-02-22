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


## Certification Path Discovery

[text here]

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

