---
layout: page
collection: fpki
title: Path Discovery and Validation
permalink: fpki/pdval/
sticky_sidenav: true
sidenav: fpki

subnav:
  - text: What Is PDVAL?
    href: '#what-is-pdval'
  - text: How Are Paths Built?
    href: '#how-are-paths-built'
  - text: What Certificate Fields Impact Path Building?
    href: '#what-certificate-fields-impact-path-building'
  - text: What Is Revocation Checking?
    href: '#what-is-revocation-checking'
    
---


## What Is PDVAL?
Before using a public key contained in a certificate, a relying party first has to determine the authenticity of that certificate and, specifically, the validity of all the certificates leading to a trusted public key, called a trust anchor. To do this, a two-step process called path discovery and validation (PDVAL), also called path processing, is performed:

1.	Trust Path Discovery – Establishes a certification path, which is an ordered list of certificates starting with a certificate that can be validated by one of the relying party's trust anchors and ending with the certificate to be validated (the target certificate).

2.	Trust Path Validation – Checks each certificate in the certification path to see that it has been properly signed, has not expired, and has not been revoked; also includes other checks on things such as name or path constraints, key usage, and extended key usage.

> **_Note:_** _Performing PDVAL helps an application make an informed trust decision (i.e., determine whether a certificate is appropriate for use in a particular application context)_.

The diagram below provides an example of a simple certification path, with three tiers in the hierarchy. The Identity Certificate is the target certificate that represents a human subscriber or a device. An example of a target certificate is an end-entity digital signature certificate on a user’s PIV Card.  The Root Certificate is the trust anchor, which is a CA’s self-signed certificate trusted by other relying parties. The Intermediate Certificates are from CAs that have signed other CA certificates along the path or the target certificate itself. These CAs are often referred to as issuing CAs. There may be multiple Intermediate Certificates in a certification path between the target and the root.

[![Example of a Certification Path](../../../assets/fpki/pivcertificatechain.png){:style="float:center"}](../../../assets/fpki/pivcertificatechain.png){:target="_blank"}{:rel="noopener noreferrer"}

## Certification Path Discovery
Without valid certification paths, certificates cannot be validated and therefore cannot be trusted.  

Path building implementations can be configured in different ways.  Some implementations may be more efficient (e.g., faster to complete), more successful (e.g., returns paths more likely to pass validation), or may yield the longest path with the most validity checks.

Ideally, the path building algorithm is optimized with priorities to guide path decision-making, is capable of building paths successfully regardless of PKI structure, and can find all possible valid paths. 
 
 > **_Note:_** _Even with an ideal, optimized algorithm, more than one path may need to be built before the best path is identified and provided to the validation step_.

### What Is Best Path?
The best certification path is typically the shortest path most likely to validate. The longer a path becomes, the greater the potential dilution of trust in the certification path. The longer and more complicated a path, the less likely it is to validate because of basic constraints, policies or policy constraints, name constraints, CRL availability, or even revocation.

### How Are Certificates Found?
Path building finds certificates in the relying party’s local repositories and cache. It also uses locations specified in the certificates it inspects during live path construction. For example, the algorithm may use: 

- **Authority Information Access (AIA) Extension** which indicates how to access CA information and services for the issuer of the certificate in which the extension appears;  
- **cACertificate attribute** of the issuing CA's directory entry to identify where self-issued certificates are stored;
- **issuedToThisCA element** of the cross-certificate pair attribute of that CA's directory entry to identify where all certificates issued to a CA (except for self-issued certificates) are stored; and
- **issuedByThisCA element** of the cross-certificate pair attribute of the issuing CA's directory entry to identify where all certificates issued by a CA to a non-subordinate or peer CA are stored.

Intermediate Certificates may be retrieved by any means available. This includes LDAP, HTTP, SQL, a local cache or certificate store, or as part of the security protocol itself, as is common practice with signed S/MIME messages and SSL/TLS sessions.

> **_Note:_** _A path may be discovered dynamically each time as needed or it may be constructed once and stored (or cached). PDVAL products may vary in how they choose to implement this operation_.

### How Is a Certification Path Chained Together?
#### Subject/Issuer Name Chaining
Path construction is done by following the Subject Name/Issuer Name connection between certificates. Moving from the trust anchor to the target certificate, the Subject Name in one certificate must be the Issuer Name in the next certificate in the path, and so on.

#### SKID/AKID Chaining
When name chaining is not sufficient, the Authority Key Identifier (AKID) and Subject Key Identifier (SKID) connection can be used to enhance path construction. 

AKIDs distinguish one public key from another when a given CA has multiple signing keys. SKIDs identify certificates that contain a specific public key. Between a trust anchor and a target certificate, the SKID of the first certificate should be the AKID of the next certificate in the path, and so on.

### Forward vs. Reverse Certification Paths
Certification paths can be constructed in the forward direction (from target certificate to trust anchor), the reverse direction (from trust anchor to target certificate), or a combination of both. The decision is based on the PKI structure/environment.

> **_Note:_** _Deciding between forward and reverse direction paths can be an important consideration. For example, forward paths may be better suited for hierarchical PKIs and reverse paths may be better suited for distributed PKIs. Sometimes a combination of both paths may be best suited_.

### Required Inputs for Path Construction
The following are required inputs to the certification path construction process:

1.	**Target Certificate** - The target certificate itself or information to retrieve the target certificate
2.	**Trust List** – The other endpoint of the path; can consist of either:   
  a.	Trusted CA certificates   
  b.	Trusted keys and DNs; a certificate is not necessarily required

### Optional Inputs for Path Construction
Optional inputs can be used to optimize path construction. Some examples are:

1.	The time for which the certificate is to be validated
2.	Initial user acceptable policy set
3.	The complete certification path for the CA  
4.	Collection of certificates that may be useful in building the path

## Trust Path Validation
Trust path validation inspects each certificate that makes up the certification path, examining policies, constraints, and consulting the issuing CA's CRL or OCSP Responder to determine each certificate's validity status at that moment. What constitutes valid is dictated by each PKI. 

Some path validation steps (e.g., checking certificate revocation status) may be performed during certification path discovery to help find the best path sooner rather than later.

> **_Note:_** _Even if a trust path is cached, all certificates in the path should be validated in real time at the beginning of each transaction_.

### Required Inputs for Path Validation
Path validation requires the following inputs:  
- The certificate path to be evaluated, to include all relevant public keys for signature validation
- The current date/time
- The list of certificate policy object identifiers (OIDs) acceptable to the relying party (or any)
- The trust anchor of the certificate path
- Indication of whether policy mapping is allowed and if any policy OID is to be tolerated

### Path Validation Steps
Path validation can perform various checks on each certificate in the path. This includes, for example, signature validation, expiration status, revocation status, policy constraints, key usage, and path length.

The submitted path is not approved if any check fails on any certificate. Otherwise, the submitted path is approved.

## What Is Revocation Checking?
Various circumstances may cause a certificate to become invalid prior to expiration of its validity period. Circumstances include name change, employee termination, and compromise or suspected compromise of the private key. Under such circumstances, the CA needs to revoke the certificate.  
There are two common revocation checking methods:
- Certificate Revocation Lists (CRLs)
- Online Certificate Status Protocol (OCSP)

### Certification Revocation Lists
A CRL is a digitally signed and time-stamped list of revoked certificates that is signed by a CA or CRL issuer and made freely available in a public repository. Each revoked certificate is identified by its certificate serial number. 

When a certificate-using system uses a certificate (e.g., for verifying a user's digital signature), that system not only checks the certificate signature and validity but also acquires the most recent CRL and checks that the certificate serial number is not on that CRL.  

A new CRL is issued on a regular periodic basis (e.g., hourly, daily, or weekly).

> **_Note:_** _FPKI CRLs are required to be refreshed at least every 18 hours_.

### Online Certificate Status Protocol
OCSP can provide more timely revocation information than is possible with CRLs and may also be used to obtain additional status information. Other benefits of OCSP over CRLs include smaller file size and greater efficiency for high-volume transactions.

An OCSP client issues a status request to an OCSP Responder and suspends acceptance of the certificates in question until the Responder provides a response. More than one target certificate may be included in a request. A requestor may choose to sign the OCSP request.

An OCSP request includes:
- **Protocol version** – OCSP protocol version
- **Service request** – One or more single certificate status requests
- **Target certificate identifier** – Serial number of each certificate in the service request
- **Optional extensions** – Which may be processed by the OCSP Responder (e.g., serviceLocator extension used to route the request to the OCSP server known to be authoritative for the identified certificate)

OCSP returns a definitive response message composed of:
- Version of the response syntax
- Identifier of the responder
- Time when the response was generated
- Responses for each of the certificates in the request
- Optional extensions
- Signature algorithm OID
- Signature computed across a hash of the response

The response for each of the certificates in a request consists of:
- **Target certificate identifier** – The serial number of the certificate
- **Certificate status value** – Specifies whether a certificate is good, revoked, or unknown (if revoked, includes the time at which the certificate was revoked and, optionally, the reason why it was revoked)   
  o	**_Good_** - Certificate currently within its validity interval is not revoked  
  o	**_Revoked_** - Certificate has been revoked, either temporarily or permanently  
  o	**_Unknown_** - OCSP Responder doesn't know about the certificate, usually because the request indicates an unrecognized issuer that is not served by this responder
- **Validity interval** – The validity interval of the response
- **Optional extensions** – Adds additional information to the response (e.g., CRLid extension used to indicate the CRL on which a revoked or onHold certificate is found)

> **_Note:_** _The "Revoked" status indicates that a certificate with the requested serial number should be rejected and the "Unknown" status indicates that the status could not be determined by this Responder, thereby allowing the relying party to decide whether it wants to try another source of status information (such as a CRL)_.
