---
layout: page 
title: Federal PKI Activity Report
collection: fpki
permalink: /fpki/tools/fpkiar/
sticky_sidenav: true
sidenav: fpkitools

subnav:
    - text: Federal Agency and Affiliate PKI Status Summary
      href: '#federal-agency-and-affiliate-pki-status-summary'
    - text: FPKIMA Certificate Activity
      href: '#fpkima-certificate-activity'
    - text: Repository Availability
      href: '#repository-availability'
---

Updated: March 7, 2022

This report provides a technical and policy compliance status for each Federal Public Key Infrastructure (FPKI) Affiliate.

- [Federal Agency and Affiliate PKI Status Summary](#federal-agency-and-affiliate-pki-status-summary)
- [FPKIMA Certificate Activity](#fpkima-certificate-activity)
- [Repository Availability](#repository-availability)

Resolve issues by contacting one of the teams:  

- Technical issues: Contact the [FPKIMA Team](mailto:fpki-help@gsa.gov) 
- Certificate Policy issues: Contact the [Certificate Policy Working Group (CPWG)](mailto:fpkipa_cpwg@listserv.gsa.gov)  

## Federal Agency and Affiliate PKI Status Summary
The operational status for each Federal Agency or affiliate connected to the Federal Common Policy CA (FCPCA) or the Federal Bridge CA (FBCA) is summarized below. The overall operational status identifies issues that affect technical interoperability and non-compliance with applicable Certificate Policies (CP). The status is not used for any other purpose such as ranking or rating.

| Federal Agency or Affiliate PKI | FPKIMA CA | Status |
| ------------------------------- | --------- | ------ |
| CertiPath Bridge | FBCA | No Issues |
| Department of Defense | FBCA | No Issues |
| DigiCert/Symantec NFI	| FBCA | No Issues |
| Entrust Managed Services NFI | FBCA | No Issues |
| Exostar NFI | FBCA | No Issues |
| Government Printing Office | FBCA | No Issues |
| IdenTrust NFI | FBCA | No Issues |
| WidePoint/ORC NFI | FBCA | No Issues |
| SAFE Identity Bridge | FBCA | No Issues |
| STRAC Bridge | FBCA | No Issues |
| TSCP Bridge | FBCA | No Issues |
| US Patent and Trademark Office (PTO) | FBCA | No Issues |
| Department of State | FCPCA | No Issues |
| DigiCert/Symantec/Verisign SSP | FCPCA | No Issues |
| Entrust Managed Services SSP | FCPCA | No Issues |
| WidePoint/ORC SSP | FCPCA | No Issues |
| Department of the Treasury | FCPCA | No Issues |
| Verizon Business SSP | FCPCA | No Issues |

## FPKIMA Certificate Activity
The activity listed in this section is limited to the certificates issued BY or TO the Federal Bridge or Federal Common Policy CA.

The following certificates were issued or published to the FPKI Trust Infrastructure in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Issued Date |
| --------- | ---------- | ---------- | --------------------- | ----------- |
| STRAC | STRAC Bridge Root Certification Authority | Federal Bridge CA G4 | Serial: 17fa12e69b7047fe09f5e465cefd3d4e62b499c9 Hash: 4a1cfa5661875b476a0c0ed57516181a67a191ca | 2/8/22 |
| DigiCert | DigiCert Federated ID L3 CA | Federal Bridge CA G4 | Serial: 175395887e9ea454697879d6acee30ddc333010f Hash: db41e72d1f5e1bd5349d4c9f45375fe01afbf2b6 | 2/8/22 |

The following certificates were removed from the FPKI Trust Infrastructure in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| STRAC | STRAC Bridge Root Certification Authority | Federal Bridge CA G4 | Serial: 1232058ae7987cc9ff3daa78c7b80813b840e12d Hash: c6d4d588000e823cfaf2ecf551ebcd3827fd71b6 | 2/14/22 | Removed Expired |
| DigiCert | DigiCert Federated ID L3 CA | Federal Bridge CA G4 | Serial: 17eaffeebc2f01cf5538b875d6b6b584fa88e27f Hash: 28f059e2dffac9de78fb7a1670c082dad2522d3b | 2/28/22 | Removed Expired |

The following certificates are planned for a certificate action in the near future, dates to be determined based on availability.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | --------------- | ------ |
| DigiCert | DigiCert Federated ID CA - G2 | Federal Bridge CA G4 | Serial:TBD      Hash:TBD |   | New CA (Rekey) 3/`6/22 |
| DigiCert | DigiCert Federal SSP Intermediate CA - G6 | Federal Common Policy CA G2 | Serial:TBD      Hash:TBD |   | New CA (Rekey) 3/16/22 |


## Repository Availability 
Repository availability is an uptime metric for Certificate Revocation List availability, based on monitoring by the FPKIMA. The table only contains Certification Authorities directly signed by the Federal Common Policy Root CA, Federal Common Policy Root G2 or Federal Bridge CA G4. A metric of "99" in the table below means the Certificate Revocation List was available for 99% of the given month, in other words, the file was not available for 1% of the month. The last column is the 12-month average.

| Federal Agency or Affiliate CA | FPKIMA CA | Last 30 days | Average |
| ------------------------------ | --------- | ------------ | ------- |
| CertiPath Bridge CA - G3 | FBCA | 100 | 100 |
| DigiCert Federated ID L3 CA | FBCA | 100 | 100 |
| DigiCert Class 3 SSP Intermediate CA - G4	| FBCA | 100 | 100 |
| DoD Interoperability Root CA 2 | FBCA	| 100 | 99.00|
| Entrust Managed Services NFI Root CA | FBCA |	100 | 100 |
| Exostar Federated Identity Service Root CA | FBCA	| 100 |	100 |
| Federal Bridge CA G4 | FBCA | 100	| 100 |
| GPO PCA | FBCA | 99.50 | 99.87 |
| IdenTrust Global Common Root CA 1 | FBCA | 99.54 | 99.84 |
| SAFE Identity Bridge CA	| FBCA | 100 | 100 |
| STRAC Bridge Root Certification Authority	| FBCA | 100 | 99.98 |
| Symantec Class 3 SSP Intermediate CA - G3	| FBCA | 100 | 81.69 |
| TSCP SHA256 Bridge CA	| FBCA | 100 | 95.42 |
| USPTO_INTR_CA1 | FBCA	| 100 | 99.95 |
| WidePoint NFI Root 2	| FBCA	| 100 |	100 |
| DigiCert SSP CA - G5	| FCPCA	| 100 |	99.1 |
| Entrust Managed Services Root CA	| FCPCA	| 99.83 | 99.98 |
| Federal Common Policy CA	| FCPCA	| 100 |	100 |
| Federal Common Policy CA G2 | FCPCA | 100 | 100 |
| ORC SSP 4	| FCPCA	| 100 | 100 |
| Symantec SSP Intermediate CA - G4	| FCPCA | 100 | 98.71 |
| U.S. Department of State AD Root CA | FCPCA | 100 | 99.85 |
| US Treasury Root CA | FCPCA | 99.98 | 100 |
| Verizon SSP CA A2 | FCPCA	| 100 | 99.96 |
| WidePoint ORC SSP 5	| FCPCA	| 100 | 100 |

