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

**Card Selection and Pin Entry – Symptom:** 
Smart card icon is not displayed; user is not prompted for PIN.

**Possible Cause 1:** 
Windows does not detect either the reader or the card due to a software or hardware issue with the card reader.

**Steps to Diagnose Cause 1:**
1.	Ask the user to make sure that the PIV card is fully inserted in the reader.
2.	If the smart card reader is an external USB device, ask the user to remove the device and try inserting it into a different USB port.
3.	Ask the user to try rebooting their workstation.
4.	Ask the user to try using their PIV with their PIN elsewhere.
5.	If the issue persists through reboot, and the PIV with PIN works elsewhere, the smart card reader may need to be replaced or the workstation may need to be serviced.

**Steps to Resolve Cause 1:**
Replace the smart card reader if it is an external device. Otherwise, schedule workstation repair.

**Possible Cause 2:**
The PIV is damaged.

**Steps to Diagnose Cause 2:**
If faulty workstation hardware or software is ruled out, and the card does not work on other readers, the PIV will need to be replaced. 

**Steps to Resolve Cause 2:** 
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
[![A screenshot of an error log. It includes several labels, including Operational and Event 104, Security-Kerberos. The Details tab is open and includes details about Event 104.]({{site.baseurl}}/assets/piv/pivath-operational-log.png)]({{site.baseurl}}/assets/piv/ pivath-operational-log.png){:target="_blank"}{:rel="noopener noreferrer"} 
 
### Steps to Resolve Cause 1
#### On the domain controller:



## 4. Name Mapping and PIV Validation

[content here]

## 5. Client Logon and Caching

[content here]
