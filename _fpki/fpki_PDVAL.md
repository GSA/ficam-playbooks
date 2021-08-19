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

## Certification Path Discovery
Without valid certification paths, certificates cannot be validated and therefore cannot be trusted.  

Path building implementations can be configured in different ways.  Some implementations may be more efficient (e.g., faster to complete), more successful (e.g., returns paths more likely to pass validation), or longest path with the most validity checks.

Ideally, the path building algorithm is optimized with priorities to guide path decision making, is capable of building paths successfully regardless of PKI structure, and can find all possible valid paths. 
 
 > **_Note:_** _Even with an ideal, optimized algorithm, more than one path may need to be built before the best path is identified and provided to the validation step_.

## What is Best Path?
The best certification path is typically the shortest path most likely to validate.  The longer a path becomes, the greater the potential dilution of trust in the certification path. The longer and more complicated a path, the less likely it is to validate because of basic constraints, policies or policy constraints, name constraints, CRL availability, or even revocation.

## How are Certificates Found?
Path building finds certificates in the relying party’s local repositories and cache.  It also uses locations specified in the certificates it inspects during live path construction.  For example, the algorithm may use: 

- **Authority Information Access (AIA) Extension** which indicates how to access CA information and services for the issuer of the certificate in which the extension appears.  
- **cACertificate attribute** of the issuing CA's directory entry to identify where self-issued certificates are stored;
- **issuedToThisCA element** of the cross-certificate pair attribute of that CA's directory entry to identify where all certificates issued to a CA (except for self-issued certificates) are stored; and
- **issuedByThisCA element** of the cross-certificate pair attribute of the issuing CA's directory entry to identify where all certificates issued by a CA to a non-subordinate or peer CA are stored.

Intermediate Certificates may be retrieved by any means available.  This includes LDAP, HTTP, SQL, a local cache or certificate store, or as part of the security protocol itself as is common practice with signed S/MIME messages and SSL/TLS sessions.

> **_Note:_** _A path may be discovered dynamically each time as needed or it may be constructed once and stored (or cached). PDVAL products may vary in how they choose to implement this operation_.


Sources may include:
[RFC 5280 (chapter 6)](https://datatracker.ietf.org/doc/html/rfc5280#page-71)
[RFC 4158](https://datatracker.ietf.org/doc/html/rfc4158)
[RFC 6960](https://datatracker.ietf.org/doc/html/rfc6960)
