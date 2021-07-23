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

---


#Windows

[Initial Brain Dump - 07232021]

1. Trust Store Management Issues
   - NTAuth does not contain issuing CA certificate
   - NTAuth does not contain issuer of DC certifciate
   - User workstation unable to validate PIV certificate
   - Domain Controller unable to validate PIV certificate 
   - User workstation unable to validate DC certificate
   - Domain Controller unable to validate its own certificate (expiration)

2. Network Configurations
   - CRL/OCSP/AIA traffic blocked
   - Tuning related misconfiguration 

3. Account Linkinking 
   - AltSecID or upn imporperly formatted


