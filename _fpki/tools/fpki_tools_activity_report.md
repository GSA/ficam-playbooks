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

Updated: February 2, 2023 

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
| WidePoint	| WidePoint NFI Root 2 | Federal Bridge CA G4 | Serial:13a7eda47618daa676730aefaa86d5986966eaf5 Hash:fadaf283e8839c5f296b9eebb00bc6cf848646f2 | 1/10/23 | 1/10/26 | 
| CertiPath | CertiPath Bridge CA - G3 | Federal Bridge CA G4 | Serial:152f481a78a3f94e3626e0507f30336378014b6c Hash:6f9f85401ac97654fa815206ebdbc0656c7903bc | 1/10/23 | 1/10/26 |

Certificates removed from the FPKI Trust Infrastructure Repository in the last 30 days.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | ----------- | ----------- |
| WidePoint	| WidePoint NFI Root 2 | Federal Bridge CA G4 | Serial:11dd76c9f15569ee0810d5af6e3d5aa104b343f5 Hash:b0b49b217bce1b18fb374dc629d5f100ba9dde49 |	2/4/23 | Renewed |
| CertiPath	| CertiPath Bridge CA - G3 | Federal Bridge CA G4 | Serial:146bc4c37a7753b792ae772067de692f093c6df1 Hash:7d6cf512ec6054e9ddf37a37d83c4955228e21c | 2/18/23 | Renewed |
| TSCP | Federal Bridge CA G4 | TSCP SHA256 Bridge CA | Serial:0bf647c7bc7ef5293968884b35105803 Hash:cc2f344b6c6965073129342f761dc9d55f6ae3fe | 1/15/23 | Removed |

The following certificates are planned for a certificate action in the near future; dates to be determined based on availability.

| Affiliate | Subject CA | Issuing CA | Serial # & SHA-1 Hash | Expiration Date | Action |
| --------- | ---------- | ---------- | --------------------- | --------------- | ------ |
| Exostar | Exostar Federated Identity Service Root CA 2 | Federal Bridge CA G4 | Serial:16c8691eec73f84d2db6d0ccb58bc8675cf0220e Hash:3930a7c9ce718d0994394feea49a4ada1ebf665d | 2/25/23 | Renewal 2/7/23 |


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
| U.S. Department of State AD Root CA | FCPCA | 98.17 |
| US Treasury Root CA | FCPCA | 86.65* |
| Verizon SSP CA A2 | FCPCA	| 100 |
| WidePoint ORC SSP 5	| FCPCA	| 100 |

*May have been related to a temporary issue with IPv6 at the hosted repository
