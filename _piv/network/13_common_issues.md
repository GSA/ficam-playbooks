---
layout: page
collection: piv
title: Troubleshooting PIV Auth Issues
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
---

## Trust Stores
PKI based mutual authentication issues often arrive when a host (e.g., a domain contoller) and client (e.g., a workstation) are not capable of establishing trust.  Given the path discovery and validation (PDVAL) processes take place within both machines, potential errors due to multiple scenarios with either machine.

   - Domain Controller (Host)
      - Domain Controller unable to validate PIV certificate
      - NTAuth does not contain PIV root CA certificate
      - NTAuth does not contain PIV intermediate or issuing CA certificate
      - Domain Controller unable to validate its own certificate (expiration) 
   - User Workstation (Client)
      - User workstation unable to validate PIV certificate 
      - NTAuth does not contain DC root CA certificate
      - NTAuth does not contain DC intermediate or issuing CA certificate

In these instances you may want to view the other end-entity certificate on the opposite machine and check the certifiation path to determine if there are errors in path validation.  If errors are encountered, you may have to modify each trust store (Root and Intermeidate CAs) to include the needed CAs from trust path.

## Network Misconfigurations
Due to required security controls many networks appliances are equiped with stringent IP whitelists that may be blocking publicly avaialble PKI resources such as Authority Information Access (AIA) points, Credential Revocation List (CRL) distrobution points, or Online Certificate Status Protocol (OCSP) responder addresses.  Common issues related to network limitations may include:

   - Revocation data such as CRL or OCSP traffic being blocked
   - Path buidling data such as SIA or AIA traffic being blocked
   - [Network Tuning](/../network/tuning){:target="_blank"} related misconfiguration such as CRL download time limits

You may need to coordinate with your network or active directory administrators to allow traffic to/from certain IP addresses or make changes to relevant group policies as needed.

## Account Linking 
Sometimes, even though hosts and clients might be able to complete mutual PKI authentication as designed, other downstream issues may arise that can prevent successful PIV use for network access.  Primarily these issues may lie with unique identification of the credential and its correlation to a network account.  Some of specific issues with unique identification may include:

  - AltSecID or User Principal Name (UPN) imporperly formatted
  - User selects improper certificate during authentication

You can visit our [network account](/../network/account){:target="_blank"} page for additional guidance in these situations.

## Helpful Tools

Microsoft Windows based systems have the ability to record logs associated with PKI and X.509 based events, called CryptoAPI v2.0 or CAPI2.  This utility can be very helpful when enabled on a domain controller host or a client machine in identifying issues with PKI processes.  

In order to enable CAPI2 logging on a Windows system, use the following steps (these may vary by Windows OS or Server version):
  1. Start button --> Windows System folder --> select Windows Administrative Tools (this navigation can also be replaced by using the search utility for "Event Viewer")
  2. Launch Event Viewer --> expand the Applications and Services Logs folder --> expand the Microsoft folder --> expand the Windows folder --> expand the CAPI2 folder --> select the Operational Llog
  3. Under the Actions pane --> select "Enable Log" option

[![Screenshot of the CAPI2 Operational Event Viewer]({{site.baseurl}}/assets/piv/CAPI2_logging.png){:style="float:left"}]({{site.baseurl}}/assets/piv/CAPI2_logging.png){:target="_blank"}{:rel="noopener noreferrer"}

Once the CAPI2 logs are enabled you may need to view the log properties to ensure the log limit is modified to capture logs relevant to your local IT administration policies or procedures, and that they are properly archvied, if needed.

After PKI events are captured you can then filter CAPI2 logs to identify specific issues you may be experiencing.  Helpful filtering options can include only viewing PKI errors and limiting the results to specific users or computers.  Some common errors seen in CAPI2 logs can include:
  - Build Chain: this can indicate improperly configured trust stores or inability to fetch AIA or SIA certifiate bundles from the internet
  - Verify Revocation: this can indicate either an inability to download CRL or verify an OCSP response or a lack of availaiblity for live revocation information
  - Verify Chain Policy: this indicates that the certificate may not have a directly expressed or mapped certificate policy verifiable up to the trust anchor

Do note that CAPI2 logs will include **all** PKI and X.509 events, to include things like:
- TLS certificate validation for user visited websites.
- code signing certificates for software updates.
- Microsoft trust store updates.

As a result, it may be a challenge to pinpoint specific error assoicated with smartcard logon; however, you can also filter results by event sources, in which case selecting **Winlogon**, may be able to target more useful errors.

[![Screenshot of the CAPI2 Operational Event Filter capability]({{site.baseurl}}/assets/piv/CAPI2_log_filtering.png){:style="float:left"}]({{site.baseurl}}/assets/piv/CAPI2_log_filtering.png){:target="_blank"}{:rel="noopener noreferrer"}

For additional information on CAPI2 logging you can view the following [Microsoft article](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-vista/cc749296(v=ws.10)?redirectedfrom=MSDN){:target="_blank"}{:rel="noopener noreferrer"}.
