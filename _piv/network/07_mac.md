---
layout: page
collection: piv
title: MacOS Considerations
permalink: piv/network/mac/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
    - text: Authentication Models
      href: '#authentication-models'
    - text: Directory Preperation
      href: '#directory-preperation'
    - text: Mac Device Configuration
      href: '#device-configuration'
    - text: Helpful References
      href: '#helpful-references'
---


### Considerations for MacOS and Network Authentication
As Federal IT networks and system expand, and especially in light of recent Bring-Your-Own-Device (BYOD) models gaining in popularity, it has become necessary to extend mandatory security controls to previously unsupported for devices.  This guide aims to provide implementation considerations for enabling mandatory Smartcard authentication on Mac workstations and laptops for access to your domains and local computer accounts, as needed.

{% include alert-warning.html heading="Mac OS Version Support" content="Smartcard logon has been supported within the Mac Operating System since macOS Sierra (10.12), and Windows Server Directory logon has been natively available since macOS High Seirra (10.13). All instructions contained within this guide assume the implmeenter is leveraving High Sierra or newer Mac Operating Systems. %}

{% include alert-success.html content="Enablement of mandatory Smartcard logon for all Mac workstations and laptios within your environment will provide the benefit of alignment to NIST SP 800-53 Identification and Authentication family of controls and thus FISMA compliance." %} 

## Authentication Models
Machine-Based Enforcement (MBE)

User-Based Enforcement (UBE)

## Directory Preperation
Device groups

Attribute mapping

## Mac Device Configuration
Smartcard Payload

Smartcard Middleware

Trust Store Management

## Helpful References
