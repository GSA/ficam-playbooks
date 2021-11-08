---
layout: page
collection: piv
title: Troubleshooting PIV Authentication Issues
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

This document describes the troubleshooting process for PIV Authentication errors to support personnel responsible for troubleshooting PIV access issues. 

Because PIV leverages PKI certificates for logical access, all PIV authentication is mutual PKI authentication. Web sites use client authenticated TLS, while other systems such as Active Directory may use different mechanisms. However, all mutual PKI authentication involves four checks:
Can the server and client both prove they control their respective private keys?
Are the server and client certificates issued from a trusted authority?
Are the server and client certificates still valid? That is, are they expired or revoked?
Is the mapping between the identifier in the certificate and the account identifier in the system still accurate?
A failure in each of these steps will display different systems in different areas. This guide will show where support personnel can locate these errors.

## Validating Private Key Access
TODO: Identify errors
Client - Wrong Pin, or issue with authentication to card
Server - missing key or incorrect private key password - server usually will not start - 500 error

## Validating that certificates are issued from a trusted authority
## Trust Stores
PKI-based mutual authentication errors often occur when a server (e.g., a domain controller) and client (e.g., a workstation) cannot establish trust between themselves. Since path discovery and validation (PDVAL) processes occur within both machines, potential errors may arise on either end of the connection.

   - Server errors
      - Server unable to validate the client's PIV certificate
      - Server certificate store does not contain a PIV root CA certificate
      - Server certificate store does not contain PIV intermediate or issuing CA certificates
      - Server Certificate Expired 
   - Client
      - Client unable to validate the server's PIV certificate 
      - Client certificate store does not contain a PIV root CA certificate
      - Client certificate store does not contain PIV intermediate or issuing CA certificates

To identify these issues, you should view the other host's certificate and attempt to validate it to identify any errors in path validation.  If the errors encountered are due to missing root or intermediate CA certificates, you should locate the absent certificate and insert it into the client or server trust store.

## Network Misconfigurations
Path discovery and validation require clients and servers to access various external systems, such as Authority Information Access (AIA) URLs, Certificate Revocation List (CRL) distribution points, or Online Certificate Status Protocol (OCSP) responders.
In highly secure environments, firewalls or other network devices may block these external ports or systems. Common issues related to network filtering may include:

   - Revocation data such as CRL or OCSP traffic being blocked
   - Path buidling data such as SIA or AIA traffic being blocked
   - [Network Tuning](/../network/tuning){:target="_blank"} related misconfiguration such as CRL download time limits

You may need to coordinate with your network or active directory administrators to allow traffic to/from specific IP addresses or make changes to relevant group policies as required.

## Verifying certificate validity
TODO: Same as Trusted?

## Verifying link between certificate subject and system account
## Account Linking 
Sometimes, even though servers and clients complete mutual PKI authentication successfully, other issues arise that prevent the successful use of PIV credentials.  Frequently, the issue is a problem with the mapping between the identifier in the PIV certificate and the local account identifier for the user.  Some common, specific issues with identifier mapping include:

  - AltSecID or User Principal Name (UPN) is improperly formatted
  -The user selects the wrong certificate during authentication

You can visit our [network account](/../network/account){:target="_blank"} page for additional guidance in these situations.

## Helpful Tools

Microsoft Windows-based systems record logs associated with PKI and X.509 based events, called CryptoAPI v2.0 or CAPI2.  These logs are helpful to identify PKI processes issues when enabled on a domain controller host or a client machine.  

To enable CAPI2 logging on a Windows system, use the following steps (these may vary by Windows OS or Server version):
  1. Start button --> Windows System folder --> select Windows Administrative Tools (alternatively, press the Start button and type "Event Viewer")
  2. Launch Event Viewer --> expand the Applications and Services Logs folder --> expand the Microsoft folder --> expand the Windows folder --> expand the CAPI2 folder --> select the Operational Log
  3. Under the Actions pane --> select the "Enable Log" option

[![Screenshot of the CAPI2 Operational Event Viewer]({{site.baseurl}}/assets/piv/CAPI2_logging.png){:style="float:left"}]({{site.baseurl}}/assets/piv/CAPI2_logging.png){:target="_blank"}{:rel="noopener noreferrer"}

Once the CAPI2 logs are enabled, you may need to configure the log limit to rotate, overwrite, or archive logs, if needed.

After CAPI2 logs are enabled, you can explore them to identify specific issues.  Helpful filtering options include only viewing PKI errors and limiting the results to particular users or computers.  Some common errors seen in CAPI2 logs include:
  - Build Chain: this can indicate improperly configured trust stores or inability to fetch AIA or SIA certificate bundles from the internet
  - Verify Revocation: this can indicate either an inability to download CRL or verify an OCSP response or a lack of availability for live revocation information
  - Verify Chain Policy: this indicates that the certificate may not have a directly expressed or mapped certificate policy verifiable up to the trust anchor

{% include alert-warning.html heading = "CAPI2 Logging" content=" CAPI2 logs will consist of all PKI and X.509 events, to include things like web certificate validation, code signing certificates for software updates, and Microsoft trust store updates." %} 

Do note that CAPI2 logs will include **all** PKI and X.509 events, such as:
- TLS certificate validation for user visited websites.
- code signing certificates for software updates.
- Microsoft trust store updates.

Filtering events to display only events with the source **Winlogon**  will help pinpoint authentication errors in the logs.

[![Screenshot of the CAPI2 Operational Event Filter capability]({{site.baseurl}}/assets/piv/CAPI2_log_filtering.png){:style="float:left"}]({{site.baseurl}}/assets/piv/CAPI2_log_filtering.png){:target="_blank"}{:rel="noopener noreferrer"}

For additional information on CAPI2 logging you can view the following [Microsoft article](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-vista/cc749296(v=ws.10)?redirectedfrom=MSDN){:target="_blank"}{:rel="noopener noreferrer"}.