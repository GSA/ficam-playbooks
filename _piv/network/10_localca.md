---
layout: page
collection: piv
title: Local Certification Authority
permalink: piv/network/localca/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
   - text: Prerequisites
     href: '#prerequisites'
   - text: Install CA Role
     href: '#install-ca-role'
   - text: Configure Certificate Template for Domain Controller
     href: '#configure-certificate-template-for-domain-controller'
   - text: Auto-Enroll Domain Controllers Using Group Policy Object (GPO)
     href: '#auto-enroll-domain-controllers-using-group-policy-object-gpo'
---

This page provides some tips for using a local certification authority (CA) to issue a domain controller certificate.  This is for local Microsoft CAs. Other platforms may be used and have different procedures.    

{% include alert-info.html content="These procedures are accurate for using Microsoft 2012 Server, Standard Edition, for CA and domain controller servers as of March 2017." %}  

<div class="usa-alert usa-alert--error" role="alert">
  <div class="usa-alert__body">
    <h4 class="usa-alert__heading">Can federally operated certificate revocation services (CRL, OCSP) operate on port 80?</h4>
    <p class="usa-alert__text">
      Yes. This very narrow class of services, that provide CRL and OCSP information for the purposes of verifying the revocation status of certificates used to make other HTTPS connections, should abide by best practices in the field and their respective specifications. For CRLs, follow 
      <a class="usa-link" href="https://tools.ietf.org/html/rfc5280" target="_blank" rel="noopener noreferrer">RFC 5280</a>
      which states CAs <strong>SHOULD NOT</strong> include URIs that specify https, ldaps, or similar schemes in extensions. For OCSP, follow 
      <a class="usa-link" href="https://tools.ietf.org/html/rfc6960" target="_blank" rel="noopener noreferrer">RFC 6960</a>
      which states a CA may use port 443 for OCSP where privacy is a requirement. Agencies are encouraged to operate OCSP and CRL services via hostnames specifically reserved for those services, so that other related information and functionality can be served securely and privately. For more information see the 
      <a class="usa-link" href="https://https.cio.gov/guide/#are-federally-operated-certificate-revocation-services-crl-ocsp-also-required-to-move-to-https" target="_blank" rel="noopener noreferrer">Federal CIO Council HTTPS-Only Standard</a>
      .
    </p>
  </div>
</div>

## Prerequisites  

  * The server that hosts the CA must be joined to the domain.
  * The CA should **never** reside on the same server(s) that are acting as domain controller(s).
  * You must be an Enterprise Administrator in the domain to perform these steps.

## Install CA Role

  1. Log into the **CA server** as a member of the **Enterprise Administrators** group.
  2. Open the **Server Manager** and click on **Manage -&gt; Add Roles and Features**.
  3. Proceed through the **Add Roles and Features Wizard** options. Choose the following:<br/>
     _Server Roles:_ **_Active Directory Certificate Services_**<br/>
     _AD CS Roles Services:_ **_Certification Authority_**<br/>
  4. On the **Results** page, click on **Configure Active Directory Certificate Services on the destination server**.
  5. Proceed through the **AD CS Configuration** options. Choose the following values, as required:<br/>
     _Role Service:_ **_Certification Authority_**<br/>
     _Setup Type:_ **_Enterprise CA_**<br/>
     _CA Type:_ **_Root CA_**<br/>
     _Private Key:_ **_Create a new private key_** <br/>
     _Cryptography:_ **_RSA#Microsoft Software Key Storage Provider, 2048 bit, SHA-256 6e_**<br/>
     _CA Name: Use the naming convention:_ **dc=[_AD suffix_], dc=[_AD domain_], cn=[_certification authority name_]**<br/>
      (e.g., dc=_gov_, dc=_[AgencyName]_, cn=_[AgencyName]_ _NPE_ _CA1_)<br/>
     _Validity Period:_ **_6 years_**<br/>
     _Certificate Database:_ **_&lt;your preference&gt;_**<br/>

## Configure Certificate Template for Domain Controller  
The domain controller(s) certificate must contain valid information. These steps provide recommended options and settings.

  1. Log into the CA server as a member of the **Enterprise Administrators** group.
  2. Open the certificate template's **MMC snap-in** (i.e., **certtmpl.msc**). 
  3. Right-click on the **Domain Controller Authentication** template. Then, click on **Duplicate Template**.
  4. Under the **Compatibility** tab, modify the **Compatibility Settings** for both the _CA_ and _certificate recipients_ to the highest compatible version (e.g., **Windows Server 2012 R2** or **Windows 2008 R2**).
  5. Under the **General** tab, use these recommended settings:<br/>
     _Template Name:_  **_&lt;Your organization&gt; - Domain Controller Authentication_**.<br/>
     _Validity Period:_  **_3 years_**.<br/>
     _Renewal Period:_  **_6 weeks_**.<br/>
  6. Under the **Cryptography** tab, set these values:<br/>
     _Minimum Key Size:_  **_2048_**.<br/>
     _Request Hash:_  **_SHA256_** <br/>
  7. Open the **CA console** (i.e., certsrv.msc).
  8. In the **console tree**, click on the **_[CA's name]_**.
  9. In the **details** pane, double-click on **Certificate Templates**.
 10. In the **console tree**, right-click on **Certificate Templates**. Then, click on **New &gt; Certificate Template To Issue**.
 11. Select and enable the **_certificate template_** that was created. Click on **OK**.

## Auto-Enroll Domain Controllers Using Group Policy Object (GPO)

  1. Log into a **Domain Controller server** as a member of the **Enterprise Administrators** group.
  2. Open the **GPMC**: gpmc.msc
  3. Within the appropriate **GPO** applied to the Domain Controllers, go to **Computer Configuration\Policies\Windows Settings\Security Settings\Public Key Policies**\ 
  4. Configure **Certificate Services Client – Auto-Enrollment** with the following options:<br/>
     _Configuration Model:_ **_Enabled_**.<br/>
     _Renew Expired Certificates, Update Pending Certificates, Remove Revoked Certificates_: **_Check_all checkboxes_**.<br/>
     _Update Certificates That Use Certificate Templates_: **_Check the checkbox_**.<br/>
  5. Replicate the group policy. Use the command: **_gpupdate /force_** at the command line, or wait for the group policy to replicate based on your replication time and settings.
  6. Open **MMC.exe -&gt; File -&gt; Add/Remove Snap-in -&gt; Certificates -&gt; Computer account -&gt; Local computer**. 
  
  If successful, you will see a new domain controller certificate in the **_Certificate (Local Computer) -&gt; Personal -&gt; Certificates folder_**. At the **Certificate Template** tab, you will also see a certificate generated with the custom certificate template.

