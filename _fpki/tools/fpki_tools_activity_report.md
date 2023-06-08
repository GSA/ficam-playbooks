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

Updated: June 8, 2023 

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
| DoD | DoD Interoperability Root CA 2 | Federal Bridge CA G4 | Serial:17a0f13585bbcfaa0d56f5041897029ee690020b Hash:eacd48fc71861e25223deea1815f49483fc1b07d | 6/8/23 | 2/7/26  | 

Certificates removed from the FPKI Trust Infrastructure Repository in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| DoD |  DoD Interoperability Root CA 2 | Federal Bridge CA G4 | Serial:101476387f77177c883bbb461f9d14d85363c472 Hash:0136b2be0a25e807fdd90300c695ab58de214dfb | 7/11/23 | Renewed |

The following certificates are planned for a certificate action in the near future; dates to be determined based on availability.

| Affiliate |   Subject CA   | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | -------------- | ---------- | --------------------- | --------------- | ------ |
| GPO |   GPO PCA   | Federal Bridge CA G4 | Serial:195cb9376d0a7dea78ab51500fd5f74a85a5f602 Hash:52db35c57036a5641bb8dd6b552391a7815681dd | 6/25/23 | Removal TBD |
| Entrust | Entrust Managed Services Root CA | Federal Common Policy CA G2 | Serial:215e78d99648b021c6394a6566d8e00f46a1e595 Hash:07f5dc58f83778d5b5738a988292c00a674a0f40 | 8/14/29 | Issue after rekey TBD |



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
| STRAC Bridge Root Certification Authority	| FBCA | 99.04 |
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

