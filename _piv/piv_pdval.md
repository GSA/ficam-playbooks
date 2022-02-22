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

[text here]

## What Is a Certification Path?

[text here]

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

