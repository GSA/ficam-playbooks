---
layout: page
collection: piv
title: macOS Considerations
permalink: piv/network/mac/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
    - text: Authentication Models
      href: '#authentication-models'
    - text: Directory Preperation
      href: '#directory-preperation'
    - text: Device Configuration
      href: '#device-configuration'
    - text: Helpful References
      href: '#helpful-references'
---


### Considerations for macOS and Smartcard Authentication
As Federal IT networks and system expand, and especially in light of recent Bring-Your-Own-Device (BYOD) models gaining in popularity, it has become necessary to extend mandatory security controls to previously unsupported devices.  This guide aims to provide implementation considerations for enabling mandatory smartcard authentication on mac operating system (macOS) based workstations and laptops for access to your domains and local computer accounts, as needed.

{% include alert-warning.html heading="Mac OS Version Support" content="Smartcard logon has been supported within the macOS since Sierra 10.12, and Windows Server Directory logon has been natively available since High Seirra 10.13. All instructions contained within this guide assume the implmenter is leveraving High Sierra or more recent macOS." %}

{% include alert-success.html content="Enablement of mandatory Smartcard logon for all Mac workstations and laptops within your environment will provide the benefit of alignment to NIST SP 800-53 Identification and Authentication family of controls and supports FISMA compliance." %} 

## Authentication Models
When users logon to workstations or laptops, they can either authenticate to a **local user account** that limits access to just the resources on the computer, or they can authenticate to a **network account** that can expand access to other domain level resources.  It is recommended, especially for Government Furnished Equipement (GFE), that smartcard based athentication be enforced for both account types.  There are two primary models for enforcing smartcard only authentication to include:

- Machine-Based Enforcement (MBE): This implmentation completely removes the option for password-based authentication in favor of Smartcard only authentication, for any account accessible by the macOS device (local or network)
- User-Based Enforcement (UBE): This implmentation creates an exception to Smartcard only authetnication to specified users or groups of users (e.g., network admins, device admins, individuals waived from smartcard requirements, etc.)

Apple support provides some additional detail on MBD vs. UBE in the [following article](https://support.apple.com/guide/deployment-reference-macos/configuring-macos-smart-cardonly-apdd3d1cd57d/web){:target="_blank"}{:rel="noopener noreferrer"}.
Additional details on [Windows authentication enforcement models](../../group){:target="_blank"} are also available in this playbook.

## Directory Preperation
Enforcing smartcard only authentication for access to domain or to local accounts requires that attributes available on the smartcard are mapped a user account for the the purpose of proper identification.  

Generally speaking, most departments and agencies already maintain processes to map PIV attributes to Active Directory network accounts.  If needed, this playbook also provides guiance on the different models that can be used to [link network accounts to PIV certificate attributes](../../account){:target="_blank"}.

The macOS devices themselves may need to be configured to extract the appropriate attributes from the smartcard based certificates, the [following section](#device-configuration) contains additional detail on this process.

## Device Configuration
Smartcard Payload

Smartcard Middleware

Trust Store Management

## Helpful References
