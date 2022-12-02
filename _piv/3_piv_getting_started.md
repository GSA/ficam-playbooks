---
layout: page
collection: piv
title: Getting Started Using a PIV
permalink: piv/gettingstarted/
sticky_sidenav: true
sidenav: piv

subnav:
    - text: Card Readers
      href: '#card-readers'
    - text: Middleware
      href: '#middleware'
    - text: Middleware Definitions
      href: '#middleware-definitions'
    - text: Next Steps
      href: '#next-steps'
---

You need two items to begin using your PIV credential:

*  A [card reader](#card-readers) (hardware)
*  [Middleware](#middleware) (software) that works with your computer

{% include alert-success.html content="With just their PIV credential, a card reader, and middleware, your users can log in to websites that are PIV enabled, digitally sign email and documents and files, and encrypt!" %}

## Card Readers

A card reader is exactly what the name suggests: a piece of hardware that helps read the card.

> *A card reader is the hardware that supplies power to the chip and allows the computer operating system to talk to the PIV credential chip operating system.*

Card readers are available in many shapes and sizes to fit both the PIV credential and to plug into your computer.  There is a card reader that will work for any shape and size  computer you use, including card readers for USB and microUSB ports.  Examples of readers include fold-up readers, desk readers, keyboard readers, tablet readers, and laptop readers.

{% include alert-info.html heading="ISO 7816" content="If you need to buy a card reader for computers, you will need one that specifies support for ISO 7816." %}

You can buy a card reader for personal use from a number of commercial online retailers.  When buying card readers for your agency, you can use [GSA Advantage](https://www.gsaadvantage.gov/){:target="_blank"}{:rel="noopener noreferrer"} to directly purchase the card readers.

Before you buy a card reader, look around and ensure that you don't already have one.  A large portion of government laptops already have card readers, and desktop computers may have keyboards with built-in readers.

Mac OSX or Linux-based computers often don’t have card readers built in. If this is the case, find a card reader option that works for you. Let's move on to middleware.

## Middleware

For PIV credentials, _middleware_ refers to the computer software or drivers that allow the computer to interact with the PIV credentials to support authentication, digital signatures, encryption, and integrations with your software tools.

For common PIV credential usage scenarios, the table below outlines the _general smartcard middleware_ available as open or government source or included in operating systems for use scenarios.  Commercial options for PIV middleware are available and the list of NIST-certified PIV middleware can be viewed [here on the NIST website](http://csrc.nist.gov/groups/SNS/piv/npivp/validation.html){:target="_blank"}{:rel="noopener noreferrer"}.

{% include alert-info.html content="Consider how to support your email client software and virtual private network software, and think about which browsers are used if you're choosing middleware for all your agency enterprise users." %}

| Name              | Operating System and Versions | Support | Considerations |
| -------------             |----|----|----|
| Windows mini-driver       | Windows 7, Windows 8, Windows 10, Windows 2008, Windows 2012  | Yes | Included in Windows operating systems and requires no installation.  Does not include the functionality to perform full lifecycle management of a PIV credential.  Does not support using your PIV credential with non-Microsoft cryptographic service providers such as those used by Mozilla Firefox browser.   |
| OpenSC       | Mac OSX 10.5, Mac OSX 10.6, Mac OSX 10.7, Mac OSX 10.9, Mac OSX 10.10, Windows (32-bit and 64-bit), Linux, *nix versions vary  | Open Source | Open source software.  Limited commercial support for maintenance and patching.  Supports PKCS#11; for example, as used by Mozilla Firefox browser. Use OpenSC versions greater than 0.20.0 to reduce authentication errors to servers using TLS 1.3. |
| Smart Card Services   | Mac OSX 10.6, Mac OSX 10.7, Mac OSX 10.9, Mac OSX 10.10  | Open Source  | Open source software. Limited commercial support for maintenance and patching.   |
| CoolKey   | Linux, *nix versions vary  | Open Source  |   |
| CACKey   | Linux, *nix versions vary  | US Government Source  | Available from Forge.mil |
| **Commercial options**   | Varies  | Yes  |  Review support for your usage needs such as email signing, encryption, network authentication, VPNs, and website authentication  |


You may need to consider network authentication, Virtual Private Network (VPN), email signing, email encryption, document signing, document encryption and website authentication when choosing one or more middleware options for yourself or your users.  In most cases, you can choose a middleware option that works for the most common uses for your purposes or mix and match based on operating systems and devices.

### Middleware Definitions

_Middleware_ as a general computer term can encompass any software that provides integration points for an application. In the standards for PIV credentials, the term _PIV middleware_ is used. A common question is "What is the difference between PIV middleware and general smart card middleware?" To simplify, we'll define the two terms as we use them for PIV credentials in these guides:

**PIV Middleware:**  

> _Client side software which implements the full set of application programming interfaces and card functions as specified in NIST Special Publication 800-73-4 and has been certified as compliant with the NIST Special Publication 800-85A series testing procedures.  The PIV compliant middleware implements all lifecycle functions, including a user's ability to perform PIN resets, activation, and renewals. The PIV compliant middleware may also implement common usage functions to support authentication, digital signatures, encryption, and integrations with multiple operating system cryptographic libraries._

**General Smart Card Middleware:**  

> _Client side software which implements common functions for an operating system and cryptographic libraries to interface with PIV credentials or other smart cards for usage.  The general smart card middleware may implement functions to support authentication, digital signatures, encryption, and integrations with multiple operating system cryptographic libraries._

For common PIV credential usage scenarios, we outline the _general smart card middleware_ available as open or government source or included in operating systems for use scenarios.  Commercial options for PIV middleware are available and the list of NIST-certified PIV middleware can be viewed [here on the NIST website](http://csrc.nist.gov/groups/SNS/piv/npivp/validation.html){:target="_blank"}{:rel="noopener noreferrer"}.


## Next Steps

You have a PIV credential, a card reader, and middleware for your computer. **Now what?**

If you want to learn more about details of PIV credentials, certificates, and how to configure a network or web application, see the [PIV Details](../details) section.
