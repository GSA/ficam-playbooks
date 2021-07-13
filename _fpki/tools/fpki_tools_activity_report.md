---
layout: page 
title: Federal PKI Activity Report
collection: fpki
permalink: fpki/tools/fpkiar/
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

Updated: June 18, 2021

This report provides a technical and policy compliance status for each Federal Public Key Infrastructure (FPKI) Affiliate.

- [FPKI Affiliate Status Summary](#fpki-affiliate-status-summary)
- [FPKI Management Authority Certificate Activity](#fpkima-certificate-activity)
- [FPKI Repository Availability](#repository-availability)

Resolve issues by contacting one of the teams:  

- Technical issues contact the [FPKIMA Team](mailto:fpki-help@gsa.gov) 
- Certificate Policy issues contact the [Certificate Policy Working Group (CPWG)](mailto:fpkipa_cpwg@listserv.gsa.gov)  

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
| SAFE BioPharma Bridge | FBCA | No Issues |
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
| N/A |  |  |  |  | 

The following certificates were removed from the FPKI Trust Infrastructure in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| FPKIMA | US Treasury Root CA | Federal Common Policy CA | Serial: 6405 Hash: 5a87922b5eaf1d63198a951b2ab6f59b2f16c131 | 8/29/21 | Revocation 6/10 |
| FPKIMA | US Treasury Root CA | Federal Common Policy CA | Serial: 734b Hash: 48ce02a99ae2cc4f790f2989aa153ed565b7e4d2 | 8/14/22| Revocation 6/10 |
| FPKIMA | Entrust Managed Services Root CA | Federal Common Policy CA | Serial: 2e26 Hash: 39c1d3b64e756a3267bfe5fecb103da892ca0611 | 7/30/25 | Revocation 6/17 |
| FPKIMA | Entrust Managed Services Root CA | Federal Common Policy CA | Serial: 734a Hash: a09655170c87d0fbfe0328b99a7baf4a1cf0b5d9 | 8/14/29 | Revocation 6/17 |

The following certificates are planned for a certificate action in the near future, dates to be determined based on availability.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | --------------- | ------ |
| N/A |  |  |  |  |  |


## Repository Availability 
Repository availability is an uptime metric for Certificate Revocation List availability, based on monitoring by the FPKIMA. The table only contains Certification Authorities directly signed by the Federal Common Policy Root CA, Federal Common Policy Root G2 or Federal Bridge CA G4. A metric of "99" in the table below means the Certificate Revocation List was available for 99% of the given month, in other words, the file was not available for 1% of the month. The last column is the 12-month average.

| Federal Agency or Affiliate CA | FPKIMA CA | Last 30 days | Average |
| ------------------------------ | --------- | ------------ | ------- |
| CertiPath Bridge CA - G2	| FBCA | 100 | 99.997 |
| CertiPath Bridge CA - G3 | FBCA | 100 | 99.98 |
| DigiCert Federated ID L3 CA | FBCA | 100 | 99.995 |
| DoD Interoperability Root CA 2 | FBCA	| 100 | 100 |
| Entrust Managed Services NFI Root CA | FBCA |	100 | 100 |
| Exostar Federated Identity Service Root CA | FBCA	| 100 |	99.987 |
| Federal Bridge CA G4 | FBCA | 100	| 100 |
| GPO PCA | FBCA | 100 | 99.838 |
| IdenTrust Global Common Root CA 1 | FBCA | 100 | 99.987 |
| SAFE Bridge CA 02	| FBCA | 100 | 99.942 |
| STRAC Bridge Root Certification Authority	| FBCA | 100 | 99.952 |
| Symantec Class 3 SSP Intermediate CA - G3	| FBCA | 100 | 99.599 |
| TSCP SHA256 Bridge CA	| FBCA | 100 | 99.992 |
| USPTO_INTR_CA1 | FBCA	| 100 | 99.949 |
| WidePoint NFI Root 2	| FBCA	| 100 |	99.992 |
| DigiCert SSP CA - G5	| FCPCA	| 100 |	99.998 |
| Entrust Managed Services Root CA	| FCPCA	| 100 | 99.998 |
| Federal Common Policy CA	| FCPCA	| 100 |	100 |
| Federal Common Policy CA G2 | FCPCA | 100 | 100 |
| ORC SSP 4	| FCPCA	| 100 | 99.993 |
| Symantec SSP Intermediate CA - G4	| FCPCA | 100 | 99.610 |
| U.S. Department of State AD Root CA | FCPCA | 98.19 | 99.847 |
| US Treasury Root CA | FCPCA | 100 | 100 |
| Verizon SSP CA A2 | FCPCA	| 100	| 99.964 |

