---
layout: page
collection: piv
title: Configure Outlook for Secure Email
permalink: /piv/user-guide/outlook/
sticky_sidenav: true
sidenav: pivuser

subnav:
    - text: Configure Outlook to Send Secure Email
      href: '#configure-outlook-to-send-secure-email'
    - text: Send a Signed Email
      href: '#send-a-signed-email'
    - text: Send an Encrypted Email
      href: '#send-an-Encrypted-email' 
    - text: Decrypt an Email
      href: '#Decrypt-an-email'
    - text: Other Helpful References
      href: '#other-helpful-references'  
      
---

Did you know that PIV cards contain digital certificates intended to help users send secure email? In general, "secure email" refers to digitally signed and/or encrypted emails.  Digitally signed emails give us confidence that the individual who claimed to send a message actually did (non-repudiation) and that the message was not modified while in transit (integrity).  Encrypted emails prevent the message from being read by unintended recipients (confidentiality).  

The following guide will walk you through configuring Outlook to leverage the digital signature and key management certificates found on your PIV to enable secure email. Be aware that by default, Outlook will only allow siganture and encryption of emails provided the configured email address on the client is same email address as encoded on a PIV.

## Configure Outlook to Send Secure Email

The following steps pertain to Microsoft Outlook 2016. 

1. Insert your PIV card in your computer's smart card reader.
2. Browse to **File** -> **Options** -> **Trust Center** -> **Trust Center Settings...** and select **Email Security**.
3. Click **Settings...** beneath the *Encrypted Email* heading.
4. Click **New** to create a new security preference.
5. Assign a *Security Settings Name* (for example, "Secure Email - PIV").
6. Click **Choose** next to *Signing Certificate*.
     - Select your PIV card's digital signature certificate and click **OK**.
     - Select **SHA256** as the *Hash Algorithm*.
7. Click **Choose** next to *Encryption Certificate*.
     - Select your PIV card's digital signature certificate and click **OK**.
     - Select **AES (256-bit)** as the *Encryption Algorithm*.
8. Enable the **Send these certificates with signed messages** selection box.
9. Click **OK** three times.

**Note:** The following screenshot shows an example of a completed security preference configuration.

[![A completed security preference configuration](../../../assets/piv/outlook-certificate-configuration.png){:style="width:85%;"}](../../../assets/piv/outlook-certificate-configuration.png){:target="_blank"}{:rel="noopener noreferrer"}

### Publish your Certificates to the Global Address List

The Global Address List (GAL) is a shared, enterprise-wide contact directory in Microsoft Outlook.  Publishing your certificates to the GAL will add your encryption certificate to an enterprise address book, making it easier for other agency users to send you an encrypted email.

1. Insert your PIV card in your computer's smart card reader.
2. Browse to **File** -> **Options** -> **Trust Center** -> **Trust Center Settings** and select **Email Security**.
3. Click **Publish to GAL...** beneath the *Digital IDs (Certificates)* heading.
4. Click **OK** when warned about Outlook publishing your default security certificates to the Global Address List.
5. Enter your PIV card PIN when prompted.
6. Click **OK** twice.

**Note:** The following screenshot shows the location of the **Publish to GAL...** button.

[![The Publish to GAL button is located in the Trust Center](../../../assets/piv/outlook-certificate-configuration-publish-gal.png){:style="width:85%;"}](../../../assets/piv/outlook-certificate-configuration-publish-gal.png){:target="_blank"}{:rel="noopener noreferrer"}

## Send a Signed Email
1. Compose an email.
2. Click the **Options** tab.
3. Enable the **Sign** icon (appears as a red ribbon icon).
4. Click **Send**.
5. Enter your PIV card PIN when prompted.

**Note:** The following screenshot shows a signed email.

[![A signed email](../../../assets/piv/outlook-certificate-configuration-signed-email.png){:style="width:85%;"}](../../../assets/piv/outlook-certificate-configuration-signed-email.png){:target="_blank"}{:rel="noopener noreferrer"}

## Send an Encrypted Email
1. Compose an email.
2. Click the **Options** tab.
3. Enable the **Encrypt** icon (appears as a yellow lock icon).
4. Click **Send**.

**Note:** It's common practice to sign a message when encrypting it, as observed below.

[![A signed and encrypted email](../../../assets/piv/outlook-certificate-configuration-encrypted-email.png){:style="width:85%;"}](../../../assets/piv/outlook-certificate-configuration-encrypted-email.png){:target="_blank"}{:rel="noopener noreferrer"}

### Manually Import a User's Encryption Certificate

When sending an encrypted email, the message is encrypted using the public key in the intended recipient's certificate.  If Outlook cannot find the intended recipient's public key through the [Global Address List](#publish-your-certificates-to-the-global-address-list), you may need to load it manually.

1. Obtain a copy of the intended recipient's [Key Management](../../details/#understand-piv-certificates) certificate (you may need to ask the intended recipient to export and share their certificate with you)
2. Click the **Home** tab.
3. Click the **Address Book**.
4. Select **File** -> **New Entry**.
5. Select **New Contact** and then click **OK**.
6. Populate the recipient's contact information, minimally including name and email address.
7. Click the **Certificates** icon.
8. Click **Import** and browse to the intended recipient's encryption certificate.
9. Click **Save & Close** and then follow the steps to [send an encrypted email](#send-an-encrypted-email).

 **Note:** The following screenshot shows a certificate loaded into a contact entry.

[![A completed contact entry.](../../../assets/piv/outlook-certificate-configuration-contact-entry.png){:style="width:85%;"}](../../../assets/piv/outlook-certificate-configuration-contact-entry.png){:target="_blank"}{:rel="noopener noreferrer"}

## Decrypt an Email

PIV users may received and store encrypted emails througout their tenure in an organization.  These emails may have been encrypted with various public key management keys that have been subsequently retired and/or replaced.  Many PIV card issuers provide historical key management keys when they issue a PIV card, but others may not.  Outlook, via the Cryptographic Application Programming Interface (CAPI), has the ability to decrypt these emails provided the associated private keys are available.  The following steps outline how to decrypt an email when the private decryption keys are available via CAPI:

1. Select an encrypted email
2. Enter your PIV card PIN or private key password when prompted

**Note:** Your organization may not recover previously issued encryption keys onto your PIV; instead, it may maintain a seperate key recovery service. Please reach out to your local IT department to determine if you can recover retired key management keys.

## Other Helpful References

- Enabling S/MIME on [Mac Mail](https://support.apple.com/guide/mail/sign-or-encrypt-emails-mlhlp1180/mac){:target="_blank"}{:rel="noopener noreferrer"}
- Enabling S/MIME on [Thurderbird email client](https://docs.nitrokey.com/pro/smime-thunderbird.html){:target="_blank"}{:rel="noopener noreferrer"}
- S/MIME with [Gmail](https://support.google.com/a/topic/9061730?hl=en&ref_topic=2683828){:target="_blank"}{:rel="noopener noreferrer"}
- S/MIME with [O365](https://support.microsoft.com/en-us/office/encrypt-messages-by-using-s-mime-in-outlook-web-app-2e57e4bd-4cc2-4531-9a39-426e7c873e26){:target="_blank"}{:rel="noopener noreferrer"}
