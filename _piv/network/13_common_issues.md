---
layout: page
collection: piv
title: Common Issues and Solutions
permalink: piv/network/solutions/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
  - text: Windows
    href: '#windows'
  - text: Trust Stores
    href: '#trust-stores'
  - text: Network Misconfigurations
    href: '#network-miconfigurations'
  - text: Account Linking
    href: '#account-linking'
  - text: Helpful Tools
    href: '#helpful-tools'


---


#Windows

## Trust Stores
PKI based mutual authentication issues often arrive when one or both parties (host and/or client) are not capable of establishing trust with each others certificates.  Given the path discovery and validation (PDVAL) processes that takes place on both party's machines this can be due to multiple scenarios with either trust store to include the following:

   - Domain Controller (Host)
      - Domain Controller unable to validate PIV certificate
      - NTAuth does not contain PIV root CA certificate
      - NTAuth does not contain PIV intermediate or issuing CA certificate
      - Domain Controller unable to validate its own certificate (expiration) 
   - User Workstation (Client)
      - User workstation unable to validate PIV certificate 
      - NTAuth does not contain DC root CA certificate
      - NTAuth does not contain DC intermediate or issuing CA certificate


## Network Misconfigurations
Due to required security controls many networks appliances are equiped with stringent IP whitelists that may be blocking publicly avaialble PKI resources such as Authority Information Access (AIA) points, Credential Revocation List (CRL) distrobution points, or Online Certificate Status Protocol (OCSP) responder addresses.

   - CRL/OCSP/AIA traffic blocked
   - Tuning related misconfiguration 

## Account Linkinking 
   - AltSecID or upn imporperly formatted

## Helpful Tools

