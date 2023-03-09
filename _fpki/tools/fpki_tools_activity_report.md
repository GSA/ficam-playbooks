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

Updated: March 7, 2023 

This report provides a technical and policy compliance status for each Federal Public Key Infrastructure (FPKI) Affiliate.

- [Federal Agency and Affiliate PKI Status Summary](#federal-agency-and-affiliate-pki-status-summary)
- [FPKIMA Certificate Activity](#fpkima-certificate-activity)
- [Repository Availability](#repository-availability)

Resolve issues by contacting one of the teams:  

- Technical issues: Contact the [FPKIMA Team](mailto:fpki-help@gsa.gov) 
- Certificate Policy issues: Contact the [Certificate Policy Working Group (CPWG)](mailto:fpkipa_cpwg@listserv.gsa.gov)  

## Federal Agency and Affiliate PKI Status Summary
If there are operational issues with a Federal Agency or affiliate connected to the Federal Common Policy CA (FCPCA) or the Federal Bridge CA (FBCA) the issues would be summarized here. Currently there are no identified issues that affect technical interoperability or non-compliance with applicable Certificate Policies (CP). 

## FPKIMA Certificate Activity
The activity listed in this section is limited to the certificates issued BY or TO the Federal Bridge or Federal Common Policy CA.

Certificates issued and published to the FPKI Trust Infrastructure Repository in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Issued Date | Expiration Date |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| DoD |Federal Bridge CA G4 | DoD Interoperability Root CA 2 | Serial:09c6 Hash:3c4b8ae115d3b46e1b03952d71404cc35ba2b2fd | 2/7/23 | 2/7/26 | 
| Exostar | Exostar Federated Identity Service Root CA 2 | Federal Bridge CA G4 | Serial:172383c4c5440fed1605c82ebc35d81518a14730 Hash:0454375f93e8da6bebde68db8e7f9ebdbba1655e | 2/7/23 | 2/7/26 |

Certificates removed from the FPKI Trust Infrastructure Repository in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| DoD |Federal Bridge CA G4 | DoD Interoperability Root CA 2 | Serial:0657 Hash:1e95e1de935599c3e7c9c72e5989665e3311d867 |	2/25/23 | Renewed |
| Exostar | Exostar Federated Identity Service Root CA 2 | Federal Bridge CA G4 | Serial:16c8691eec73f84d2db6d0ccb58bc8675cf0220e Hash:3930a7c9ce718d0994394feea49a4ada1ebf665d | 2/25/23 | Renewed |

The following certificates are planned for a certificate action in the near future; dates to be determined based on availability.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | --------------- | ------ |
| WidePoint | TBD | Federal Common Policy CA G2 | Serial:TBD Hash:TBD | 2/25/23 | Initial Issuance TBD |


## Repository Availability 
Repository availability is an uptime metric for Certificate Revocation List availability, based on monitoring by the FPKIMA. The table only contains Certification Authorities directly signed by the Federal Common Policy Root CA, Federal Common Policy Root G2, or Federal Bridge CA G4. A metric of "99" in the table below means the Certificate Revocation List was available for 99% of the given month; in other words, the file was not available for 1% of the month. 

| Federal Agency or Affiliate CA | FPKIMA CA | Last Month | 
| ------------------------------ | --------- | ------------ | 
| CertiPath Bridge CA - G3 | FBCA | 100 | 
| DigiCert Federated ID L3 CA | FBCA | 100 | 
| DigiCert Class 3 SSP Intermediate CA - G4	| FBCA | 100 |
| DoD Interoperability Root CA 2 | FBCA	| 100 |
| Entrust Managed Services NFI Root CA | FBCA |	100 |
| Exostar Federated Identity Service Root CA | FBCA	| 100 |
| Federal Bridge CA G4 | FBCA | 100	| 
| GPO PCA | FBCA | 100 | 
| IdenTrust Global Common Root CA 1 | FBCA | 100 | 
| SAFE Identity Bridge CA	| FBCA | 100 |
| STRAC Bridge Root Certification Authority	| FBCA | 100 |
| Symantec Class 3 SSP Intermediate CA - G3	| FBCA | 100 |
| TSCP SHA256 Bridge CA	| FBCA | 100 |
| USPTO_INTR_CA1 | FBCA	| 100 |
| WidePoint NFI Root 2	| FBCA	| 100 |
| DigiCert SSP CA - G5	| FCPCA	| 100 |
| Entrust Managed Services Root CA	| FCPCA	| 100 |
| Federal Common Policy CA	| FCPCA	| 100 |
| Federal Common Policy CA G2 | FCPCA | 100 |
| ORC SSP 4	| FCPCA	| 100 |
| Symantec SSP Intermediate CA - G4	| FCPCA | 100 |
| U.S. Department of State AD Root CA | FCPCA | 100 |
| US Treasury Root CA | FCPCA | 100 |
| Verizon SSP CA A2 | FCPCA	| 100 |
| WidePoint ORC SSP 5	| FCPCA	| 100 |

