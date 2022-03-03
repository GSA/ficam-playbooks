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


<table>
      <tr>
        <td style="width:250px;border:0px;"><strong> Card Selection and Pin Entry – Symptom</strong></td>
        <td style="border:0px;">Smart card icon is not displayed; user is not prompted for PIN.</td>
      </tr>
      <tr>
        <td style="width:250px;border:0px;"><strong>Possible Cause 1</strong></td>
        <td style="border:0px;">Windows does not detect either the reader or the card due to a software or hardware issue with the card reader.</td>
      </tr>
      <tr>
        <td style="width:250px;border:0px;"><strong>Steps to Diagnose Cause 1</strong></td>
        <td style="border:0px;"> 1. Ask the user to make sure that the PIV card is fully inserted in the reader.<br><b>2. If the smart card reader is an external USB device, ask the user to remove the device and try inserting it into a different USB port.</b><br>3. Ask the user to try rebooting their workstation.<bt><a href="{{site.baseurl}}/assets/piv/troubleshooting/pivauth-best-match-event-viewer.png" target="_blank" rel="noopener noreferrer"><img src="{{site.baseurl}}/assets/piv/troubleshooting/pivauth-best-match-event-viewer.png" width="308" height="87" alt=" A screenshot of the Event Viewer app icon and label. The words Best Match appear above the icon." /></a><br>4. Ask the user to try using their PIV with their PIN elsewhere.<br> &nbsp&nbsp&nbsp&nbsp&nbsp5. If the issue persists through reboot, and the PIV with PIN works elsewhere, the smart card reader may need to be replaced or the workstation may need to be serviced.</td>
      </tr>
      <tr>
        <td style="width:250px;border:0px;"><strong>Steps to Resolve Cause 1</strong></td>
        <td style="border:0px;">Replace the smart card reader if it is an external device. Otherwise, schedule workstation repair.</td>
      </tr>
      <tr>
          <td style="width:250px;border:0px;"><strong>Possible Cause 2</strong> </td>
        <td style="border:0px;"> The PIV is damaged.</td>
      </tr>
      <tr>
        <td style="width:250px;border:0px;"><strong>Steps to Diagnose Cause 2</strong></td>
        <td style="border:0px;">If faulty workstation hardware or software is ruled out, and the card does not work on other readers, the PIV will need to be replaced.</td>
      </tr>
      <tr>
        <td style="width:250px;border:0px;"><strong>Steps to Resolve Cause 2</strong></td>
        <td style="border:0px;">Replace the PIV card.</td>
      </tr>
    </table>

      



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
