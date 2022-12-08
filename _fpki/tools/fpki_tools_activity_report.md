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

Updated: December 6, 2022 

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

The following certificates were issued or published to the FPKI Trust Infrastructure in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Issued Date | Expiration Date |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| USPTO | USPTO_INTR_CA1 | Federal Bridge CA G4 | Serial:178a1e7c4919d730a80d08afd2b8fea66bdff0f6 Hash:e35da05374246a6d0a892f5eec31f74cdbd794b0 | 11/9/22 | 11/9/25 |

The following certificates were removed from the FPKI Trust Infrastructure in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| USPTO | USPTO_INTR_CA1 | Federal Bridge CA G4 | Serial:10f82e9132e31f62dba620ab66f6e7f836e663c7 Hash:edd7e56da5147cf98ea580a176a27bc990b243ce | 12/12/22 | Renewed |

The following certificates are planned for a certificate action in the near future; dates to be determined based on availability.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | --------------- | ------ |
| WidePoint | WidePoint NFI Root 2 | Federal Bridge CA G4 | Serial:11dd76c9f15569ee0810d5af6e3d5aa104b343f5 Hash:b0b49b217bce1b18fb374dc629d5f100ba9dde49 | 2/4/23 | Renewal TBD |
| CertiPath | CertiPath Bridge CA - G3 | Federal Bridge CA G4 | Serial:146bc4c37a7753b792ae772067de692f093c6df1 Hash:77d6cf512ec6054e9ddf37a37d83c4955228e21c | 2/18/23 | Renewal TBD |
| Exostar | Exostar Federated Identity Service Root CA 2 | Federal Bridge CA G4 | Serial:16c8691eec73f84d2db6d0ccb58bc8675cf0220e Hash:3930a7c9ce718d0994394feea49a4ada1ebf665d | 2/25/23 | Renewal TBD |


## Repository Availability 
Repository availability is an uptime metric for Certificate Revocation List availability, based on monitoring by the FPKIMA. The table only contains Certification Authorities directly signed by the Federal Common Policy Root CA, Federal Common Policy Root G2, or Federal Bridge CA G4. A metric of "99" in the table below means the Certificate Revocation List was available for 99% of the given month; in other words, the file was not available for 1% of the month. 

| Federal Agency or Affiliate CA | FPKIMA CA | Last 30 days | 
| ------------------------------ | --------- | ------------ | 
| CertiPath Bridge CA - G3 | FBCA | 100 | 
| DigiCert Federated ID L3 CA | FBCA | 100 | 
| DigiCert Class 3 SSP Intermediate CA - G4	| FBCA | 100 |
| DoD Interoperability Root CA 2 | FBCA	| 99.093 |
| Entrust Managed Services NFI Root CA | FBCA |	100 |
| Exostar Federated Identity Service Root CA | FBCA	| 100 |
| Federal Bridge CA G4 | FBCA | 100	| 
| GPO PCA | FBCA | 100 | 
| IdenTrust Global Common Root CA 1 | FBCA | 99.096 | 
| SAFE Identity Bridge CA	| FBCA | 100 |
| STRAC Bridge Root Certification Authority	| FBCA | 98.618 |
| Symantec Class 3 SSP Intermediate CA - G3	| FBCA | 100 |
| TSCP SHA256 Bridge CA	| FBCA | 99.988 |
| USPTO_INTR_CA1 | FBCA	| 99.932 |
| WidePoint NFI Root 2	| FBCA	| 100 |
| DigiCert SSP CA - G5	| FCPCA	| 100 |
| Entrust Managed Services Root CA	| FCPCA	| 100 |
| Federal Common Policy CA	| FCPCA	| 100 |
| Federal Common Policy CA G2 | FCPCA | 100 |
| ORC SSP 4	| FCPCA	| 100 |
| Symantec SSP Intermediate CA - G4	| FCPCA | 100 |
| U.S. Department of State AD Root CA | FCPCA | 100 |
| US Treasury Root CA | FCPCA | 99.095 |
| Verizon SSP CA A2 | FCPCA	| 100 |
| WidePoint ORC SSP 5	| FCPCA	| 100 |

