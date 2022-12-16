---
layout: page
collection: piv
title: Introduction to Network Authentication Guides
permalink: piv/network/
sticky_sidenav: true
sidenav: piv

subnav:
  - text: Network Ports and Protocols
    href: ../../piv/network/ports/
  - text: Domain Controllers
    href: ../../piv/network/dc/
  - text: Trust Stores
    href: ../../piv/network/trust-stores/
  - text: Account Linking
    href: ../../piv/network/account/
  - text: Group Policies and Enforcement
    href: ../../piv/network/group/
  - text: Network Tuning
    href: ../../piv/network/tuning/
  - text: Local Certification Authority
    href: ../../piv/network/localca/
  - text: Authentication Assurance
    href: ../../piv/network/auth/
  - text: PIV Auth on macOS
    href: ../../piv/network/mac/
  - text: Troubleshooting PIV Logon
    href: ../../piv/network/troubleshooting/    
---

<div class="usa-alert usa-alert--error" role="alert">
  <div class="usa-alert__body">
    <h4 class="usa-alert__heading">Dec 2022 - Update to Microsoft Network Authentication Issue</h4>
    <p class="usa-alert__text">
      The Microsoft KB mentioned above is updated. Note that the "disabled" mode retirement is still targeted at 2/14/23. CISA encourages any agency still reliant on "disabled" mode to move to "compatibility mode" by following the <a class="usa-link" href="https://www.cisa.gov/guidance-applying-june-microsoft-patch" target="_blank" rel="noopener noreferrer">CISA Guidance</a> as soon as possible while a timeline and plans around long term resolution of this issue is finalized with Microsoft. Additional technical guidance can be requested through cyberlaison at CISA dot DHS dot gov.
    </p>
  </div>
</div>

<div class="usa-alert usa-alert--error" role="alert">
  <div class="usa-alert__body">
    <h4 class="usa-alert__heading">May 2022 - Known PIV Network Authentication Issue</h4>
    <p class="usa-alert__text">
      Some PIV-based authentication to Microsoft Domain Controllers are impacted by May 2022 Windows server patches.  If you encounter these PIV network logon issues, please review the <a class="usa-link" href="https://www.cisa.gov/guidance-applying-june-microsoft-patch" target="_blank" rel="noopener noreferrer">CISA Guidance</a> which is supported by the following <a class="usa-link" href="https://support.microsoft.com/en-us/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16" target="_blank" rel="noopener noreferrer">KB5014754—Certificate-based authentication changes on Windows domain controllers</a> page.  Additional technical guidance can be requested through cyberlaison at CISA dot DHS dot gov.
    </p>
  </div>
</div>

These Network Authentication guides will help you configure your Windows _network domain_ for smart card logon using PIV credentials.

There are many useful pages and technical articles available online that include details on configurations and using generic smart cards.  The information presented here addresses common questions and configurations **specific** to the U.S. federal government, **PIV** smart cards, and U.S. federal civilian agency certification authorities.

{% include alert-info.html heading = "Teamwork" content="Work with your Network Engineers, Domain Admins, Account Management, and Information Security colleagues to review the information, perform the configurations, and troubleshoot any issues." %}

## Pre-Launch Checklist

Check the following items **before** reviewing these network guides and lessons learned:

1. Users have PIV credentials and PIV card readers.
1. You are using Microsoft Active Directory to manage your Windows network.
1. Domain Controllers are Microsoft 2012 or newer.
1. User workstations **are joined** to your network and are Windows 8 or Windows 10-based.

## Configuration Checklist

There are five configuration categories to review with your colleagues.  All five include steps that must be completed; it's best to review and complete the configuration categories in this order:

- [Network Ports and Protocols](../network/ports/)
- [Domain Controllers](../network/dc/)
- [Trust Stores](../network/trust-stores/)
- [Account Linking: Associating PIV credentials with User Accounts](../network/account/)
- [Group Policies and Enforcement](../network/group/)

There are five additional guides:

- [Network Tuning](../network/tuning/)
- [Local Certification Authority](../network/localca/)
- [Authentication Assurance](../network/auth/)
- [PIV Authentication on MacOS](../network/mac/)
- [Troubleshooting PIV Logon](../network/troubleshooting/)

We want to add additional information for installing Online Certificate Status Protocol (OCSP) services, addressing common errors and troubleshooting, and configuring MacOSX and other operating systems.  

Submit an [Issue]({{site.repourl}}/issues/new){:target="_blank"}{:rel="noopener noreferrer"} to identify information that would be helpful to you, or consider contributing a page to these guides with your lessons learned.
