---
layout: page
collection: piv
title:  Personal Identity Verification Guide Introduction
permalink: piv/
sticky_sidenav: true
sidenav: piv

subnav:
    - text: What Is PIV?
      href: '#what-is-piv'
    - text: What Information Is in These PIV Guides?
      href: '#what-information-is-in-these-piv-guides'
    - text: Why Is PIV Usage Important?
      href: '#why-is-piv-usage-important'
    - text: What Systems Should Use PIV?
      href: '#what-systems-should-use-piv'
    - text: Where Can I Find the Standards?
      href: '#where-can-i-find-the-standards'
    - text: How Can I Test a PIV Card?
      href: '#how-can-i-test-a-piv-card'     
---

These **Personal Identity Verification (PIV) Guides** are intended to help you implement common PIV configurations at your organization. These guides are [open source]({{ site.repourl }}){:target="_blank"}{:rel="noopener noreferrer"} and a _work in progress_ and we [welcome contributions](https://www.idmanagement.gov/contribute/){:target="_blank"}{:rel="noopener noreferrer"} from our colleagues.

The guides focus on using PIV credentials for _logical access_ such as authenticating to networks or applications or digitally signing and encrypting. Using PIV for _physical access_ is available in the [PACS Guide]({{site.baseurl}}/pacs/){:target="_blank"}{:rel="noopener noreferrer"}.

If you cannot find a particular topic, it may still be in development. Review the [Issues]({{ site.repourl }}/issues){:target="_blank"}{:rel="noopener noreferrer"} for questions and lessons that are in progress. Create a new [Issue]({{ site.repourl }}/issues/new){:target="_blank"}{:rel="noopener noreferrer"} to ask a question or share information with others.  

Read on to learn more about PIV credentials.

## What Is PIV?

A PIV credential is a U.S. federal government-wide credential used to access federally controlled facilities and information systems at the appropriate security level.

PIV credentials have certificates and key pairs, pin numbers, biometrics like fingerprints and pictures, and other unique identifiers.  When these items are put together in a PIV credential, the credential provides the capability to implement multifactor authentication for networks, applications, and buildings.

## What Information Is in These PIV Guides?  
First, we cover the basics of PIV credentials, including:

-   What PIV is, contains, and looks like;
-   The basics of getting started with PIV credentials; and
-   Using PIV for network authentication (smart card logon). 

We also cover applications and guidance for developers and users—which need your input!  
{% include alert-success.html heading = "Share your expertise" content="Please contribute and share your lessons for configuring systems or applications, tuning considerations, code, common challenges, troubleshooting errors, and anything else you think would be helpful for your colleagues." %}

## Why Is PIV Usage Important?

Agency security is enhanced when PIV credentials are used for authentication to agency systems and facilities. PIV credentials allow for a high level of assurance in the individuals that access your resources, because the credentials are only issued by trusted providers to individuals that have been verified in person. PIV credentials are highly resistant to identity fraud, tampering, counterfeiting, and exploitation.

PIV credentials are _standardized_ as well. PIV credentials might be issued by different organizations using different commercial or open source products, on different form factors (cards, mobile devices, etc.).  However, PIV credentials are standardized——every PIV credential is required to have specific information, using technology that is _interoperable_.

Your PIV credential from one agency will have the same basic required format, information, and technology as a PIV credential from your partner agencies. This allows us to trust each other, share applications, and architect and implement systems using common patterns for authentication.

## What Systems Should Use PIV?  
Any system at your organization that requires heightened security for determining who should gain access can and should use PIV for authentication. While PIV credentials can be used for authentication on almost any system, they are especially useful for systems that protect sensitive information.

PIV should be used for:

* All authentication for all _privileged_ users, including servers, networks, and applications;
* All _network_ authentication for _all_ users;
* All application authentication for _all_ users of an application that protects or contains sensitive information; and
* Access to facilities and buildings.

## Where Can I Find the Standards? 

Review the information on this site if you are interested in PIV credentials or work on _using_ PIV credentials.

If you are interested in the bits and bytes of PIV credentials, you can review the standards (see below), particularly if you develop products such as hardware or software that are _specific_ to PIV credentials for the U.S. federal government. (For most users and engineers, the standards may be too detailed for your needs.)

To review the standards, there is a [National Institute for Science and Technology (NIST) website](http://csrc.nist.gov/groups/SNS/piv/standards.html){:target="_blank"}{:rel="noopener noreferrer"} with all PIV-related standards. Here are links to some of the most common standards:

- [**FIPS-201**](https://csrc.nist.gov/publications/detail/fips/201/2/final){:target="_blank"}{:rel="noopener noreferrer"} specifies the issuance and management of PIV credentials.
- [**NIST Special Publication 800-73, "Interfaces for Personal Identity Verification"**](https://csrc.nist.gov/publications/detail/sp/800-73/4/final){:target="_blank"}{:rel="noopener noreferrer"} specifies the interface and data elements of PIV credentials.
- [**NIST Special Publication 800-76, "Biometric Data Specification for Personal Identity Verification"**](https://csrc.nist.gov/publications/detail/sp/800-76/2/final){:target="_blank"}{:rel="noopener noreferrer"} specifies the technical acquisition and formatting requirements for biometric data of PIV credentials.

## How Can I Test a PIV Card?

The [Card Conformance Tool (CCT)](https://github.com/GSA/piv-conformance/wiki/User-Guide){:target="_blank"}{:rel="noopener noreferrer"} can remotely test PIV and Personal Identity Verification–Interoperable (PIV-I) on several common operating systems. The purpose of the CCT is to validate that commercially available PIV and PIV-I comply with relevant standards.
