---
layout: page
collection: piv
title: Common Issues and Solutions
permalink: piv/network/solutions/
sticky_sidenav: true
sidenav: pivnetwork

subnav:

  - text: Trust Stores
    href: '#trust-stores'
  - text: Network Misconfigurations
    href: '#network-miconfigurations'
  - text: Account Linking
    href: '#account-linking'
  - text: Helpful Tools
    href: '#helpful-tools'
  - text: Windows
    href: '#windows'


---


#Windows

## Trust Stores
PKI based mutual authentication issues often arrive when one or both parties (host and/or client) are not capable of establishing trust with each others certificates.  Given the path discovery and validation (PDVAL) processes that takes place on within both parties, potential errors can be due to multiple scenarios with either machine to include the following:

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

   - Revocation data such as CRL or OCSP traffic being blocked
   - Path buidling data such as SIA or AIA traffic being blocked
   - [Tuning](/../tuning){:target="_blank"} related misconfiguration such as CRL download time limits

## Account Linkinking 
   - AltSecID or upn imporperly formatted

## Helpful Tools
###Windows
Microsoft Windows based systems have the ability to record logs associated with PKI and X.509 based events, called CryptoAPI v2.0 or CAPI2.  This utility can be very helpful when enabled on a domain controller host or a client machine in identifying issues with PKI processes.  

In order to enable CAPI2 logging on a Windows system, use the following steps (these may vary by Windows OS or Server version):
  1. Start button --> Windows System folder --> select Windows Administrative Tools (this navigation can also be replaced by using the search utility for "Event Viewer")
  2. Launch Event Viewer --> expand the Applications and Services Logs folder --> expand the Microsoft folder --> expand the Windows folder --> expand the CAPI2 folder --> select the Operational Llog
  3. Under the Actions pane --> select "Enable Log" option

Once the CAPI2 logs are enabled you may need to view the log properties to ensure the log limit is modified to capture logs relevant to your local IT administration policies or procedures, and that they are properly archvied, if needed.

After PKI events are captured you can then filter CAPI2 logs to identify specific issues you may be experiencing.  Helpful filtering options can include only viewing PKI errors and limiting the results to specific users or computers.

For additional information on CAPI2 logging you can view the following [Microsoft article](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-vista/cc749296(v=ws.10)?redirectedfrom=MSDN){:target="_blank"}{:rel="noopener noreferrer"}.
