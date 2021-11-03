---
layout: page
collection: piv
title: macOS Considerations
permalink: /piv/network/mac/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
    - text: Authentication Models
      href: '#authentication-models'
    - text: Directory Preparation
      href: '#directory-preparation'
    - text: Device Configuration
      href: '#device-configuration'
    - text: Helpful References
      href: '#helpful-references'
---


As federal IT networks and systems expand, and especially in light of recent Bring-Your-Own-Device (BYOD) models gaining in popularity, it has become necessary to extend mandatory security controls to previously unsupported devices.  This guide aims to provide implementation considerations for enabling mandatory smartcard authentication on mac operating system (macOS)-based workstations and laptops for access to your domains and local computer accounts, as needed.

{% include alert-warning.html heading="macOS Version Support" content="Smartcard logon has been supported within the macOS since Sierra 10.12, and Windows Server Directory logon has been natively available since High Sierra 10.13. All instructions contained within this guide assume the implementer is leveraging High Sierra or a more recent macOS." %}

{% include alert-success.html heading="Compliance Support" content="Enablement of mandatory smartcard logon for all Mac workstations and laptops within your environment will provide the benefit of alignment to the NIST SP 800-53 Identification and Authentication family of controls and will support FISMA compliance." %} 

## Authentication Models
When users logon to workstations or laptops, they can either authenticate to a **local user account** that limits access to just the resources on the computer, or they can authenticate to a **network account** that can expand access to other domain level resources.  It is recommended, especially for Government Furnished Equipment (GFE), that smartcard-based athentication be enforced for both account types.  There are two primary models for enforcing smartcard only authentication: 

- Machine-Based Enforcement (MBE): This implementation completely removes the option for password-based authentication in favor of smartcard only authentication for any account accessible by the macOS device (local or network)
- User-Based Enforcement (UBE): This implementation creates an exception to smartcard only authentication for specified users or groups of users (e.g., network admins, device admins, individuals waived from smartcard requirements, etc.)

Apple support provides some additional detail on MBE vs. UBE in the [following article](https://support.apple.com/guide/deployment-reference-macos/configuring-macos-smart-cardonly-apdd3d1cd57d/web){:target="_blank"}{:rel="noopener noreferrer"}.
Additional details on [Windows authentication enforcement models](../group){:target="_blank"} are also available in this playbook.

## Directory Preparation
Enforcing smartcard only authentication for access to domain or to local accounts requires that attributes available on the smartcard are mapped to a user account for the the purpose of proper identification.  

Generally speaking, most departments and agencies already maintain processes to map PIV attributes to Active Directory network accounts.  This playbook also provides guidance on the different models that can be used to [link network accounts to PIV certificate attributes](../../account){:target="_blank"}.

The macOS devices themselves may need to be configured to extract the appropriate attributes from the smartcard-based certificates. The [following section](#3.-other-configurations-and-software) contains additional details on this process.

## Device Configuration
Configuration of the actual macOS workstations and laptops can vary between implementing organizations; however, only a few mechanisms can deliver needed configuration profiles (known as property lists or .plist) to the target device, which may include:

- Employing third party Mobile Device Management (MDM) tools
- Leveraging an [Apple specific configuration tool](https://apps.apple.com/us/app/apple-configurator-2/id1037126344?mt=12){:target="_blank"}{:rel="noopener noreferrer"} via the App Store
- Direct configuration profile delivery via one of several avenues, such as:
    - delivery via an email,
    - from a webpage, or
    - using [over-the-air profile delivery](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/iPhoneOTAConfiguration/Introduction/Introduction.html#//apple_ref/doc/uid/TP40009505){:target="_blank"}{:rel="noopener noreferrer"}

If the options above are not available, the device administrator may also leverage physical access to manually run needed [configuration commands.](https://support.apple.com/guide/deployment-reference-macos/advanced-smart-card-options-apd2969ad2d7/web){:target="_blank"}{:rel="noopener noreferrer"}

Several changes may be needed to ensure compliance with organizational IT policies. These configurations can be categorized as follows:

### 1. [Smartcard-Relevant Configurations](https://developer.apple.com/documentation/devicemanagement/smartcard){:target="_blank"}{:rel="noopener noreferrer"}
This category includes configurations that are needed to appropriately enforce use cases associated with smartcard authentication, such as:
- allowSmartCard - must be set to TRUE to allow the device to leverage smartcards for multiple functions (authentication, digital signing, etc.) 
- enforceSmartCard - can be set to TRUE to ensure that smartcard authentication is made mandatory at initial logon, authorization, and unlocking from screensaver mode
- tokenRemovalAction - if set to "1," enables the screensaver when a smartcard is physically removed from the device
- UserPairing - can be set to FALSE to prevent the pairing dialogue from appearing on smartcard insertion
- oneCardPerUser - can be set to FALSE for users who may have multiple acceptable smartcards (e.g., PIV and alternative tokens)
- checkCertificateTrust - can be an integer between 0 and 3:
    - 0 - turns off certificate trust checking
    - 1 - turns on trust checking, but does not conduct revocation checking
    - 2 - turns on trust checking, and a 'soft' revocation check is conducted where 'valid' and 'unknown' are treated the same
    - 3 - turns on trust checking, and a 'hard' revocation check is conducted where the response must contain a 'valid' status to allow the authentication to proceed


### 2. Trust Store Management
As part of the authentication protocols that take place between a device with a smartcard and a domain controller, all certificates in use need to be validated.  This includes validation of the certificates contained on the smartcard used for authentication and validation of the domain controller device certificate.  

As a result of this needed certificate validation, the device trust store must be able to conduct path discovery and validation (PDVAL) on both certificates, requiring their trust anchors to be installed on the target device.  For the purpose of leveraging PIV certificates, administrators will want to ensure that the [Federal Common Policy Certification Authority G2 certificate](http://repo.fpki.gov/fcpca/fcpcag2.crt){:target="_blank"}{:rel="noopener noreferrer"} is included in those trust store updates.  Additionally, the root certificate of the domain contoller device certificate will also need to be included.

{% include alert-warning.html heading="Domain Controller Certificate Trust" content="Many organizations run internal device PKIs that issue their domain controller certificates.  Do not assume that installing the FCPCA G2 certificate into macOS keychains will facilitate smartcard login." %}

### 3. Other Configurations and Software
In order to leverage smartcard authentication for network accounts, the device must also be configured to present the appropriate identifiers from the smartcard PKI certifiate for matching to a network account.  The following image provides the contents of a configuration file that extracts the NT Principal Name from a PIV to match against a directory AltSecID in support of an authentication event.

[![P List configuration for extracting a network account identifier from a PIV]({{site.baseurl}}/assets/piv/attribute_mapping_plist.png){:style="float:left"}]({{site.baseurl}}/assets/piv/attribute_mapping_plist.png){:target="_blank"}{:rel="noopener noreferrer"}

Local account logon via smartcard may also require that the unique identifiers from a smartcard are mapped to a local user record.  Scripting can be leveraged to look up a user Principal Name from a public directory and subsequently update the local user record with the identifier.

> script placeholder
> placeholder line 2

Other configurations might be needed on the target device, such as loading preferred middleware for interfacing with the smartcard.  Note that CrytoTokenKit has the ability to interface with most PIVs and comes native with macOS 10.12 and later.

## Helpful References
