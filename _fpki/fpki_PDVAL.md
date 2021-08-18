---
layout: page
collection: fpki
title: Path Discovery and Validation
permalink: fpki/pdval/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: What is PDVAL?
    href: '#what-is-pdval'
  - text: How are Paths Built?
    href: '#how-are-paths-built'
  - text: What certificate fields impact path building?
    href: '#what-certificate-fields-impact-path-building'
  - text: What is Revocation Checking?
    href: '#what-is-revocation-checking'
    
---
# Path Discovery and Validation

## What is PDVAL
Before using a public key contained in a certificate, a relying party first has to determine the authenticity of that certificate, and specifically, the validity of all the certificates leading to a trusted public key, called a trust anchor. To do this, a two-step process called path discovery and validation (PDVAL), also called path processing, is performed:

1.	Trust Path Discovery – establishes a certification path, which is an ordered list of certificates starting with a certificate that can be validated by one of the relying party's trust anchors, and ending with the certificate to be validated (the target certificate).

2.	Trust Path Validation – checks each certificate in the certification path to see that it has been properly signed, has not expired, and has not been revoked; also includes other checks on things such as name or path constraints, key usage, and extended key usage.

> **_Note:_** _Performing PDVAL helps an application make an informed trust decision – i.e., determine whether a certificate is appropriate for use in a particular application context_.

The diagram below provides an example of a simple certification path, with 3 tiers in the hierarchy. The Identity Certificate is the target certificate that represents a human subscriber or a device. An example of a target certificate is an end-entity digital signature certificate on a user’s PIV Card.  The Root Certificate is the trust anchor, which is a CA’s self-signed certificate trusted by other relying parties. The Intermediate Certificates are from CAs that have signed other CA certificates along the path or the target certificate itself. These CAs are often referred to as issuing CAs.  There may be multiple Intermediate Certificates in a certification path between the target and the root.

[![Example of a Certification Path](../../../assets/fpki/pivcertificatechain.png){:style="float:center"}](../../../assets/fpki/pivcertificatechain.png){:target="_blank"}{:rel="noopener noreferrer"}

## How are Paths Built
subject/issuer name matching, SKI/AKI matching, 

## What Certificate Fields Impact Path Building
Date processing/validity periods, path constraints, policy constrints, etc.

## What is Revocation Checking
outline how CRLs and OCSP work at a high level

Sources may include:
[RFC 5280 (chapter 6)](https://datatracker.ietf.org/doc/html/rfc5280#page-71)
[RFC 4158](https://datatracker.ietf.org/doc/html/rfc4158)
[RFC 6960](https://datatracker.ietf.org/doc/html/rfc6960)
