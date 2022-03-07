---
layout: page
collection: piv
title: Troubleshooting Windows Smart Card Logon with PIV Authentication 
permalink: piv/network/troubleshooting/
sticky_sidenav: true
sidenav: pivnetwork

subnav:
    - text: Logon Process Overview
      href: '#logon-process-overview'
    - text: 1. Process Start
      href: '#1-process-start'
    - text: 2. Card Selection and PIN Entry
      href: '#2-card-selection-and-pin-entry'
    - text: 3. Credential Authentication and Secure Connection to Logon Server
      href: '#3-credential-authentication-and-secure-connection-to-logon-server'
    - text: 4. Name Mapping and PIV Validation
      href: '#4-name-mapping-and-piv-validation'
    - text: 5. Client Logon and Caching
      href: '#5-client-logon-and-caching'   
---

Within the federal enterprise, Windows smart card logon with a PIV card is the baseline capability used to satisfy Federal Information Security Management Act (FISMA) and National Institute of Standards and Technology (NIST) Risk Management Framework policy requirements regarding authentication. A PIV card enables high-assurance, two-factor authentication to a Windows desktop. Under normal conditions, this system is simple and easy for an end user to use. However, if this logon mechanism breaks, it can be difficult to troubleshoot logon and authentication errors. This page includes common symptoms and suggested steps to diagnose and solve these issues.

## Logon Process Overview

The figure below, from the “Smart card sign-in flow in Windows” section of the [Microsoft Certificate Requirements and Enumeration article](https://docs.microsoft.com/en-us/windows/security/identity-protection/smart-cards/smart-card-certificate-requirements-and-enumeration#smart-card-sign-in-flow-in-windows){:target="_blank"}{:rel="noopener noreferrer"}, provides a detailed overview of how smart card logon works in supported versions of Windows.

[![A detailed workflow diagram of how smart card logon works in supported versions of Windows.]({{site.baseurl}}/assets/piv/pivauth-overview.png)]({{site.baseurl}}/assets/piv/pivauth-overview.png){:target="_blank"}{:rel="noopener noreferrer"}

For our use, this complex process is simplified into the following workflows:
1. [Process Start](#1-process-start)
2. [Card Selection and PIN Entry](#2-card-selection-and-pin-entry)
3. [Credential Authentication and Secure Connection to Logon Server](#3-credential-authentication-and-secure-connection-to-logon-server)
4. [Name Mapping and PIV Validation](#4-name-mapping-and-piv-validation)
5. [Client Logon and Caching](#5-client-logon-and-caching)

## 1. Process Start

Smart card logon begins at the client workstation. First, the system discovers smart card reader devices that are built into or attached to the workstation. Next, acceptable smart card logon certificates from any connected cards are provided to the Windows logon screen. In general, PIV cards issued in accordance with Federal Common Policy have been engineered to have one certificate, the PIV authentication certificate, marked eligible for smart card logon. However, in some instances, more than one certificate may have been inadvertently made eligible, meaning the user may first be asked to select the correct certificate for smart card logon. Conversely, the user may have a Facility Access Card (FAC) that omits access to any workstation. For more details on what is in use at your organization, speak with your agency’s credential issuer or ICAM representative.

[![A screenshot of a logon screen that includes icons for entering a password or inserting a smart card.]({{site.baseurl}}/assets/piv/pivauth-logon-screen.png)]({{site.baseurl}}/assets/piv/pivauth-logon-screen.png){:target="_blank"}{:rel="noopener noreferrer"}

## 2. Card Selection and PIN Entry

When the logon screen appears, if the system has detected a smart card reader and an attached (inserted) smart card with suitable certificates, the smart card logon option is displayed and the user is prompted to enter a PIN.

Use the information below to troubleshoot symptoms encountered with card selection before PIN entry.

### Card Selection and Pin Entry – Symptom 
Smart card icon is not displayed; user is not prompted for PIN.

### Possible Cause 1 
Windows does not detect either the reader or the card due to a software or hardware issue with the card reader.

### Steps to Diagnose Cause 1
1.	Ask the user to make sure that the PIV card is fully inserted in the reader.
2.	If the smart card reader is an external USB device, ask the user to remove the device and try inserting it into a different USB port.
3.	Ask the user to try rebooting their workstation.
4.	Ask the user to try using their PIV with their PIN elsewhere.
5.	If the issue persists through reboot, and the PIV with PIN works elsewhere, the smart card reader may need to be replaced or the workstation may need to be serviced.

### Steps to Resolve Cause 1
Replace the smart card reader if it is an external device. Otherwise, schedule workstation repair.

### Possible Cause 2
The PIV is damaged.

### Steps to Diagnose Cause 2
If faulty workstation hardware or software is ruled out, and the card does not work on other readers, the PIV will need to be replaced. 

### Steps to Resolve Cause 2 
Replace the PIV card.

## 3. Credential Authentication and Secure Connection to Logon Server

After the user enters their PIN, Windows tries to unlock the card using the PIN entered. 
After the card has been unlocked, the workstation packages the user’s PIV authentication certificate and sends it to the logon server, also known as a domain controller. The workstation must be able to trust the domain controller so that the workstation can securely connect to it.

Use the information below to troubleshoot symptoms encountered after the PIN is entered but before logon occurs.

### Credential Validation – Symptom 
After PIN entry, the following error is displayed on the logon screen: “Signing in with a smart card isn’t supported with your account. For more information, contact your administrator.”

### Possible Cause 1
A suitable domain controller authentication certificate is not installed on the domain controller.

### Steps to Diagnose Cause 1
#### On the client: 
1.	Log in to Windows using a password.
2.	Open the Start Menu, located in the bottom left corner of the screen.
3.	Type **event viewer**.
4.	Click **Event Viewer**, shown under Best Match.<br>
 [![A screenshot of the Event Viewer app icon and label. The words Best Match appear above the icon.]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png)]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png){:target="_blank"}{:rel="noopener noreferrer"}<br>  
5.	On the left side of the Event View, use the **>** symbol to expand each of these items on the tree:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a.	Applications and Services Logs<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b.	Microsoft<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c.	Windows<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d.	Security-Kerberos<br>
[![A screenshot of the Event Viewer app icon with several app and folder icons below it in cascading order. The Operational icon appears at the bottom of the screenshot and is highlighted with gray.]({{site.baseurl}}/assets/piv/pivauth-event-viewer-thru-operational.png)]({{site.baseurl}}/assets/piv/pivauth-event-viewer-thru-operational.png){:target="_blank"}{:rel="noopener noreferrer"}<br>
6.	Click **Operational**.
7.	On the right side of the window, under Actions, click **Enable Log** (skip this step if the option reads ”Disable Log”; the log is already enabled).<br>
[![A screenshot of several icons, labels, and item choices below the Actions heading. The Help icon and label appears at the bottom of the screenshot. In the middle of the screenshot, the Enable Log choice is highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-actions-thru-help.png)]({{site.baseurl}}/assets/piv/pivauth-actions-thru-help.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
8.	Log out of Windows.
9.	Try having the user log in to their workstation again using their PIV. 
10.	Log in to Windows using a password.
11.	Repeat Steps 2 through 6 to return to the Security-Kerberos log in Event Viewer.
12.	Click in the center of the window where ”Error” is shown. The following log will appear:<br>
[![A screenshot of an error log. It includes several labels, including Operational and Event 104, Security-Kerberos. The Details tab is open and includes details about Event 104.]({{site.baseurl}}/assets/piv/pivath-operational-log.png)]({{site.baseurl}}/assets/piv/pivath-operational-log.png){:target="_blank"}{:rel="noopener noreferrer"} 
 
### Steps to Resolve Cause 1
#### On the domain controller:
1.	Log in as a Domain Administrator.
2.	Open the Start Menu.
3.	Type **mmc.exe**.
4.	Click **MMC**, shown under Best Match.<br>
[![A screenshot of the mmc.exe icon. The words Best Match appear above the icon and the words Run command appear below the icon.]({{site.baseurl}}/assets/piv/pivauth-best-match-mmc-exe.png)]({{site.baseurl}}/assets/piv/pivauth-best-match-mmc-exe.png){:target="_blank"}{:rel="noopener noreferrer"}<br>  
5.	If prompted by a User Account Control pop-up, click **Yes**.
[![A screenshot of a User Account Control window. The words Do you want to allow this app to make changes to your device? appear near the top of the screenshot. The Yes button is highlighted.]({{site.baseurl}}/assets/piv/pivauth-user-account-control.png)]({{site.baseurl}}/assets/piv/pivauth-user-account-control.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
6.	Click the **MMC** window and press and hold **Ctrl**. Then press **M** and release both keys.
7.	In the Add or Remove Snap-ins window, click the following:<br> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a.	From the Available Snap-ins on the left, click **Certificates**.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b.	In the center of the window, click the **Add** button.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c.	In the Certificates snap-in window, click **Computer account**. Then click **Next**.<br>
[![A screenshot of an Add or Remove Snap-In window with an inset Certificate Snap-In window.]({{site.baseurl}}/assets/piv/pivauth-snap-in.png)]({{site.baseurl}}/assets/piv/pivauth-snap-in.png){:target="_blank"}{:rel="noopener noreferrer"}<br>  
8.	In the Select Computer window, click **Finish**.<br> 
[![A screenshot of a Select Computer window. The Local Computer radio button is highlighted and the Finish button is highlighted.]({{site.baseurl}}/assets/piv/pivauth-select-computer.png)]({{site.baseurl}}/assets/piv/pivauth-select-computer.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
9.	In the Add or Remove Snap-ins window, click **OK**.
10.	On the left side of the MMC window, use the **>** symbol to expand these items on the tree:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a.	Certificates (Local Computer)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b.	Personal<br>
[![A screenshot of a Console Root folder icon and label with three items below it in cascading order. A Certificates folder icon and label appear at the bottom of the screenshot and are highlighted with gray.]({{site.baseurl}}/assets/piv/pivauth-console-root-thru-certificates.png)]({{site.baseurl}}/assets/piv/pivauth-console-root-thru-certificates.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
11.	Under Personal, right-click **Certificates**.<br>  
[![A screenshot of a Console Root folder icon and label with several items and folders below it. The Certificates folder is highlighted with blue. An inset window with All Tasks highlighted in blue appears to the right of the main window and an inset Request New Certificate window appears to right of the first inset window.]({{site.baseurl}}/assets/piv/pivauth-certificates-all-tasks.png)]({{site.baseurl}}/assets/piv/pivauth-certificates-all-tasks.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
12.	Click **All Tasks**.
13.	Click **Request New Certificate**.
14.	In the Certificate Enrollment window, click **Next**.
15.	Click **Next**.
16.	Click the box next to the Domain Controller Authentication template. If you do not see this, ask your CA Administrator to publish this template.<br>
[![A screenshot of a Certificate Enrollment window. The words Request Certificates appear in blue near the top of the screenshot. The screenshot includes Active Directory Enrollment Policy choices, statuses, and details.]({{site.baseurl}}/assets/piv/pivauth-request-certificates.png)]({{site.baseurl}}/assets/piv/pivauth-request-certificates.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
17.	Click **Enroll**.
18.	Click **Finish**.<br> 
[![A screenshot of a Certificate Enrollment window. The words Certificate Installation Results appear in blue near the top of the screenshot. The screenshot includes Active Directory Enrollment Policy Domain Controller Authentication status and details. A green bar runs below the Certificate Enrollment window and the Finish button is highlighted.]({{site.baseurl}}/assets/piv/pivauth-cert-enrollment.png)]({{site.baseurl}}/assets/piv/pivauth-cert-enrollment.png){:target="_blank"}{:rel="noopener noreferrer"}

## 4. Name Mapping and PIV Validation

After the domain controller’s authentication certificate is used to make a secure link from the workstation to the domain controller, the certificate data for the user’s smart card is sent to the domain controller for validation. The domain controller does the following to validate the credential:

1.	The domain controller looks up the user’s account in Active Directory (AD) using information found in the user’s PIV authentication certificate. This process is known as name mapping. More information about user name mapping can be found in the [Account Linking playbook](https://playbooks.idmanagement.gov/piv/network/account/#transitioning-from-upn-mapping-to-altsecurityidentities-mapping){:target="_blank"}{:rel="noopener noreferrer"}. 
2.	The certificate is sent to the Microsoft Crypto-API (CAPI) service running on the domain controller for path discovery and validation. CAPI performs basic certificate checks, described in the Certification Path Discovery and Validation (PDVal) playbook. [LINK TO PDVAL PLAYBOOK WHEN IT IS COMPLETE]  
3.	The domain controller checks its local copy of the Enterprise NTAUTH store for the presence of the issuing certification authority (CA) for the PIV authentication certificate. Steps for adding a certificate to this store can be found in the [Trust Stores playbook](https://playbooks.idmanagement.gov/piv/network/trust-stores/){:target="_blank"}{:rel="noopener noreferrer"}. 

**Note:** Certificate validation of the PIV authentication certificate for smart card logon only occurs on the individual domain controller processing the logon request. The client computer does not check the validity of the logon certificate. Other applications outside of Windows logon may perform certificate validation locally, so it may still be a good idea to have a valid path installed on your organization’s client computers. if you have multiple logon servers in your environment, only the one responding to the individual logon request performs validation. Therefore, it is important to maintain a consistent configuration across your domain controllers.

Use the information below to troubleshoot additional symptoms encountered after the PIN is entered, but before logon occurs. 

### Name Mapping and PIV Validation – Symptom 1
After PIN entry, one of the following errors displays on the logon screen:<br> 
“An untrusted certification authority was detected while processing the smart card certificate used for authentication.”<br>
[![A screenshot of a logon window that includes the words An untrusted certification authority was detected while processing the smart card certificate used for authentication.]({{site.baseurl}}/assets/piv/pivauth-untrusted-ca-logon-screen.png)]({{site.baseurl}}/assets/piv/pivauth-untrusted-ca-logon-screen.png){:target="_blank"}{:rel="noopener noreferrer"}<br>
“The smart card used for authentication has been revoked.”<br>
[![A screenshot of a logon window that includes the words The smart card used for authentication has been revoked.]({{site.baseurl}}/assets/piv/pivauth-smart-card-revoked-logon-screen.png)]({{site.baseurl}}/assets/piv/pivauth-smart-card-revoked-logon-screen.png){:target="_blank"}{:rel="noopener noreferrer"}

### Possible Cause 1
The user’s PIV authentication certificate fails path discovery and validation on the domain controller.

### Steps to Diagnose Cause 1
#### On the client:
1.	Log in to Windows using a password.
2.	Open the Start Menu, located in the bottom left corner of the screen.
3.	Type **cmd**.
4.	Click **Command Prompt**, shown under Best Match.<br>
[![A screenshot of the Command Prompt app icon. The words Best Match appear above the icon.]({{site.baseurl}}/assets/piv/pivauth-best-match-command-prompt.png)]({{site.baseurl}}/assets/piv/pivauth-best-match-command-prompt.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
5.	In the command prompt, type **echo %logonserver%** and press **Enter**.<br>
[![A screenshot of a Command Prompt window that includes the Windows version and user details.]({{site.baseurl}}/assets/piv/pivauth-command-prompt.png)]({{site.baseurl}}/assets/piv/pivauth-command-prompt.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
6.	The current domain controller being used for Windows logon is displayed. This is the best domain controller to check first for troubleshooting invalid smart card logon events.

#### On the domain controller indicated above:
1.	Log in as a Domain Administrator.
2.	Open the Start Menu.
3.	Type **mmc.exe**.
4.	Log in to Windows using a password.
5.	Open the Start Menu, located in the bottom left corner of the screen.
6.	Type **event viewer**.
7.	Click **Event Viewer**, shown under Best Match.<br> 
[![A screenshot of the Event Viewer app icon and label. The words Best Match appear above the icon.]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png)]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png){:target="_blank"}{:rel="noopener noreferrer"}<br>  
8.	On the left side of the Event View, use the **>** symbol to expand each of these items on the tree:<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a.	Applications and Services Logs<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b.	Microsoft<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c.	Windows<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d.	CAPI2<br>
9.	Click **Operational**.
10.	On the right side of the window, under Actions, click **Enable Log** (skip this step if the option reads ”Disable Log”; the log is already enabled).<br>
[![A screenshot of several icons, labels, and item choices below the Actions heading. The Help icon and label appears at the bottom of the screenshot. In the middle of the screenshot, the Enable Log choice is highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-actions-thru-help.png)]({{site.baseurl}}/assets/piv/pivauth-actions-thru-help.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
11.	Log out of Windows on the client workstation.
12.	Have the user try to log in using their PIV, taking note of the time. The error should be shown on the logon screen.
13.	On the domain controller, still in Event Viewer, on the right pane, click **Refresh**.
14.	New log events will be shown. Look for the events with an “Error” status  and the task category “Build Chain.”
15.	Click the **Details** tab. In the UserData section, look for the user’s name in the Certificate [subjectName] field.<br> 
[![A screenshot of an Operational window labeled Event 11, CAPI2. In the center of the screenshot, the subjectName and user name are highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-operational-event11.png)]({{site.baseurl}}/assets/piv/pivauth-operational-event11.png){:target="_blank"}{:rel="noopener noreferrer"}<br> 
If you do not see the user’s name, continue scrolling through the list of events to find the next event with an “Error” status and the task category “Build Chain.” Using results filtering may help to narrow this list down.

16.	Once you find the event, scroll down through the details. You will see sections that say “-ChainElement.” These indicate each of the certificates in the path that was built. Within each chain element, look again for the ”- Certificate [ subjectName ],” indicating which certificate is being checked, and below it, a ”- TrustStatus” with an ”- Error Status” which will give more details about the failing validation.

**Example 1: A certificate in the path is revoked.**<br>
[![A screenshot of an Operational window labeled Event 11, CAPI2. The Certificate and the TrustStatus details are highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-example1.png)]({{site.baseurl}}/assets/piv/pivauth-example1.png){:target="_blank"}{:rel="noopener noreferrer"} 

**Example 2: The path does not build to a trust anchor.**<br>
[![A screenshot of a window labeled Event 11, CAPI2. The subjectName and the Cert Trust Is Untrusted Root details are highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-example2.png)]({{site.baseurl}}/assets/piv/pivauth-example2.png){:target="_blank"}{:rel="noopener noreferrer"} 

**Example 3: The revocation status is unreachable, or the revocation status signature cannot be validated due to an invalid trust path.**<br>
[![A screenshot of a window labeled Event 11, CAPI2. The subjectName and the Cert Trust Revocation Status Unknown details are highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-example3.png)]({{site.baseurl}}/assets/piv/pivauth-example3.png){:target="_blank"}{:rel="noopener noreferrer"} 
 
**Note:** The error status in Example 3 will occur for any certificate lower in the path than the above Examples for 1 and 2. For example, if a trusted root cannot be found at the top of the path, no valid revocation status will be found for any certificate issued below the trusted root, including the issuing CA certificate and the end user’s PIV authentication certificate. This situation occurs because the revocation data cannot have its signature verified for the same reasons that the certificate itself cannot.

### Steps to Resolve Cause 1
1.	On the domain controller, work through any path validation issues identified in the above steps and examples. Keep in mind that that path building comes before validation and that a path is built from the bottom up. In this instance, the PIV authentication certificate chains to a trust anchor, such as Federal Common Policy G2. **Ensure that the correct trust anchor for your organization’s PIV credentials is installed on every domain controller.** If you also trust certificates from other agencies and organizations, the appropriate roots and cross-certificates may need to be installed to complete the path. 
2.	Find expired and revoked certificates that may be installed in your domain controller certificate store and delete them as appropriate. In a Windows environment, unexpected errors often result if you have duplicates of a certificate installed in a given store or have accidently installed an intermediate CA in the trusted root store or vice versa. 
3.	Lastly, you will need to allow outbound access over port TCP 80 from each domain controller to each of the CRL, OCSP, and AIA distribution points listed in the certificates in the path. For more information, see the Certification Path Discovery and Validation (PDVal) playbook. [LINK TO  PDVAL PLAYBOOK WHEN IT IS COMPLETE]

### Possible Cause 2
The Issuing CA is not in the NTAuth store.

### Steps to Diagnose Cause 2
1.	Follow Steps 1 through 15 for diagnosing Possible Cause 1.
2.	Confirm that there is no error logged for the task category ”Build Chain” with matching certificate subjectName for the user.
3.	Look for an error logged for task category ”Verify Chain Policy” with matching certificate subjectName for the user.
4.	Confirm that the result logged is ”A certification chain processed correctly, but one of the CA certificates is not trusted by the policy provider.”<br>
[![A screenshot of an Operational window labeled Event 30, CAPI2. Near the top of the screenshot, a row labeled Error is highlighted with yellow. Elsewhere in the screenshot, the subjectName and user name and the Result details are highlighted with yellow.]({{site.baseurl}}/assets/piv/pivauth-operational-event30.png)]({{site.baseurl}}/assets/piv/pivauth-operational-event30.png){:target="_blank"}{:rel="noopener noreferrer"} 

### Steps to Resolve Cause 2
Follow the steps in the [Trust Stores playbook](https://playbooks.idmanagement.gov/piv/network/trust-stores/){:target="_blank"}{:rel="noopener noreferrer"} to add the appropriate issuing CA for the PIV card to the Enterprise NTAuth trust store.

## 5. Client Logon and Caching

Once name mapping and PIV validation are complete, the domain controller sends a logon package to the client computer with the user’s domain permissions and a token that allows desktop logon for that user. If the user is permitted to log in to the computer, they will now be logged into their Windows desktop.

The first logon must always occur while the system has a network connection to the domain controller, whether it is directly attached to the organization’s network or via a VPN. After the first logon, if the Group Policy setting pictured below is set to a value greater than 0, the user’s logon token will be permanently cached by their workstation as long as the number of subsequent users to log in does not exceed this number. 

[![A screenshot of a Local Group Policy Editor window with two columns of folder and item icons and labels. The screenshot includes an inset Interactive Number of previous logons to cache window.]({{site.baseurl}}/assets/piv/pivauth-local-group-policy-editor.png)]({{site.baseurl}}/assets/piv/pivauth-local-group-policy-editor.png){:target="_blank"}{:rel="noopener noreferrer"}

If a future logon is attempted while the user’s workstation is disconnected from the organization’s network, and the logon token is cached, the workstation will only authenticate the PIV authentication certificate via PIN and, upon successful entry, will log the user into their desktop using their cached token and permissions. If the value is set to 0, caching does not occur and logon will only occur when the workstation is connected to the network and can communicate with a domain controller.


