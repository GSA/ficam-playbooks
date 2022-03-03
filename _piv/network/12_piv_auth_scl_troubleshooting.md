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

## Logon Process Overview

[content here]

| Symptom/Cause | Details/Steps | 
| --------------------------------- | ----------------------------------- | 
| **Credential Validation – Symptom** | After PIN entry, the following error is displayed on the logon screen: “Signing in with a smart card isn’t supported with your account. For more information, contact your administrator.” |
| **Possible Cause 1** | A suitable domain controller authentication certificate is not installed on the domain controller. |
| **Steps to Diagnose Cause 1** | On the client:<br>1. Log in to Windows using a password.<br>2. Open the Start Menu, located in the bottom left corner of the screen.<br>3. Type **event viewer**.<br>4. Click **Event Viewer**, shown under Best Match.<br>[![A screenshot of the Event Viewer app icon and label. The words Best Match appear above the icon.]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png)]({{site.baseurl}}/assets/piv/pivauth-best-match-event-viewer.png){:target="_blank"}{:rel="noopener noreferrer"}<br>5. On the left side of the Event View, use the **>** symbol to expand each of these items on the tree:<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a. Applications and Services Logs<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b. Microsoft<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;c. Windows<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;d. Security-Kerberos<br>[![A screenshot of the Event Viewer app icon with several app and folder icons below it in cascading order. The Operational icon appears at the bottom of the screenshot and is highlighted with gray.]({{site.baseurl}}/assets/piv/pivauth-event-viewer-thru-operational.png)]({{site.baseurl}}/assets/piv/pivauth-event-viewer-thru-operational.png){:target="_blank"}{:rel="noopener noreferrer"}<br>6. Click **Operational**. |



## 1. Process Start

[content here]

## 2. Card Selection and PIN Entry

[content here]

## 3. Credential Authentication and Secure Connection to Logon Server

[content here]

## 4. Name Mapping and PIV Validation

[content here]

## 5. Client Logon and Caching

[content here]
